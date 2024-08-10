---
title: "Cómo Implementar un Back-End Simple para Web3.js Usando GraphQL y TypeScript"
description: "Aprende a configurar un back-end simple para Web3.js usando GraphQL y TypeScript, incluyendo la configuración de un servidor Node.js, definición de esquemas y resolutores de GraphQL, e integración de Web3.js."
tags: ["Web3.js", "GraphQL", "TypeScript", "Node.js", "Blockchain"]
---

## Cómo Implementar un Back-End Simple para Web3.js Usando GraphQL y TypeScript

### Requisitos Previos

1. **Node.js (v22 o superior)**
2. **Conocimientos básicos de TypeScript, GraphQL y Web3.js**

### Paso 1: Configura Tu Proyecto

1. **Inicializa el proyecto:**

   ```bash
   mkdir web3-graphql-backend
   cd web3-graphql-backend
   yarn init -y
   ```

2. **Instala las dependencias:**

   ```bash
   yarn add express express-graphql graphql type-graphql reflect-metadata web3
   yarn add --dev typescript ts-node @types/node @types/express @types/graphql
   ```

3. **Inicializa la configuración de TypeScript:**

   ```bash
   yarn tsc --init
   ```

   Actualiza `tsconfig.json` para incluir:

   ```json
   {
     "compilerOptions": {
       "target": "ES6",
       "module": "commonjs",
       "outDir": "./dist",
       "rootDir": "./src",
       "strict": true,
       "esModuleInterop": true,
       "experimentalDecorators": true,
       "emitDecoratorMetadata": true
     }
   }
   ```

### Paso 2: Configura Web3.js

1. **Crea un archivo `.env`** para almacenar tu URL de RPC de testnet y otras variables de entorno:

   ```env
   INFURA_PROJECT_ID=tu_id_de_proyecto_infura
   ```

2. **Instala dotenv para variables de entorno:**

   ```bash
   yarn add dotenv
   ```

### Paso 3: Crea el Servidor GraphQL

1. **Crea la estructura de carpetas:**

   ```bash
   mkdir -p src/graphql
   touch src/index.ts src/graphql/schema.ts src/graphql/resolvers.ts
   ```

2. **Configura Web3.js en `src/index.ts`:**

   ```typescript
   import 'reflect-metadata';
   import express from 'express';
   import { ApolloServer } from 'apollo-server-express';
   import { buildSchema } from 'type-graphql';
   import { Web3Resolver } from './graphql/resolvers';
   import dotenv from 'dotenv';
   import Web3 from 'web3';

   dotenv.config();

   const app = express();
   const web3 = new Web3(`https://mainnet.infura.io/v3/${process.env.INFURA_PROJECT_ID}`);

   async function startServer() {
     const schema = await buildSchema({
       resolvers: [Web3Resolver],
     });

     const server = new ApolloServer({ schema });

     await server.start();
     server.applyMiddleware({ app });

     app.listen(4000, () => {
       console.log('El servidor está corriendo en http://localhost:4000/graphql');
     });
   }

   startServer().catch((error) => {
     console.error('Error al iniciar el servidor:', error);
   });
   ```

### Paso 4: Define el Esquema y los Resolutores de GraphQL

1. **Crea el esquema GraphQL en `src/graphql/schema.ts`:**

   ```typescript
   import { buildSchema } from 'type-graphql';
   import { Web3Resolver } from './resolvers';

   export const schema = buildSchema({
     resolvers: [Web3Resolver],
   });
   ```

2. **Crea el resolutor en `src/graphql/resolvers.ts`:**

   ```typescript
   import { Resolver, Query, Arg } from 'type-graphql';
   import Web3 from 'web3';
   import dotenv from 'dotenv';

   dotenv.config();

   const web3 = new Web3(`https://mainnet.infura.io/v3/${process.env.INFURA_PROJECT_ID}`);

   @Resolver()
   export class Web3Resolver {
     @Query(() => String)
     async getBlockNumber(): Promise<string> {
       const blockNumber = await web3.eth.getBlockNumber();
       return blockNumber.toString();
     }

     @Query(() => String)
     async getBalance(@Arg('address') address: string): Promise<string> {
       const balance = await web3.eth.getBalance(address);
       return web3.utils.fromWei(balance, 'ether');
     }
   }
   ```

### Paso 5: Ejecuta y Prueba Tu Servidor

1. **Compila el código de TypeScript:**

   ```bash
   yarn tsc
   ```

2. **Ejecuta el servidor usando `ts-node`:**

   ```bash
   yarn ts-node src/index.ts
   ```

3. **Accede al playground de GraphQL:**

   Abre [http://localhost:4000/graphql](http://localhost:4000/graphql) en tu navegador.

### Consultas de Ejemplo

Para obtener el número de bloque actual:

```graphql
query {
  getBlockNumber
}
```

Para obtener el balance de una dirección de Ethereum:

```graphql
query {
  getBalance(address: "0x742d35Cc6634C0532925a3b844Bc454e4438f44e")
}
```

### Conclusión

Has implementado con éxito un back-end simple para Web3.js usando GraphQL y TypeScript. Esta configuración te permite ampliar tu API de GraphQL con más funcionalidades de Web3.js según sea necesario.