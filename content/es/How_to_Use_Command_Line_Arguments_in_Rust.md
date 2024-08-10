---
title: "Cómo Usar Argumentos de Línea de Comando en Rust"
description: "Aprende a manejar argumentos de línea de comando en Rust usando std::env y la crate clap, con ejemplos prácticos."
tags: ["Rust", "Argumentos de Línea de Comando", "Programación", "CLI", "Rust CLI", "Terminal"]
---

# Cómo Usar Argumentos de Línea de Comando en Rust

Los argumentos de línea de comando son una forma poderosa de influir en el comportamiento de tus programas en tiempo de ejecución. En Rust, manejar argumentos de línea de comando es sencillo y se puede hacer utilizando el módulo `std::env` o la crate `clap` para un análisis más avanzado. Esta guía te llevará a través de ambos métodos con ejemplos.

## Usando el Módulo `std::env`

El módulo `std::env` proporciona funciones para interactuar con el entorno del sistema operativo. Puedes recuperar los argumentos de línea de comando usando la función `args`, que devuelve un iterador.

### Ejemplo Básico con `std::env::args`

Aquí hay un ejemplo sencillo que imprime los argumentos de línea de comando:

```rust
use std::env;

fn main() {
    let args: Vec<String> = env::args().collect();
    
    println!("Número de argumentos: {}", args.len());
    for (i, argument) in args.iter().enumerate() {
        println!("Argumento {}: {}", i, argument);
    }
}
```

Para ejecutar este programa:

```sh
cargo run -- arg1 arg2 arg3
```

Salida:

```
Número de argumentos: 4
Argumento 0: target/debug/my_program
Argumento 1: arg1
Argumento 2: arg2
Argumento 3: arg3
```

### Analizando Argumentos

A menudo, necesitarás analizar los argumentos de línea de comando a tipos específicos. Aquí hay un ejemplo de cómo analizar dos enteros y sumarlos:

```rust
use std::env;

fn main() {
    let args: Vec<String> = env::args().collect();
    
    if args.len() != 3 {
        eprintln!("Uso: {} <num1> <num2>", args[0]);
        std::process::exit(1);
    }
    
    let num1: i32 = args[1].parse().expect("Por favor, proporciona un entero válido");
    let num2: i32 = args[2].parse().expect("Por favor, proporciona un entero válido");

    println!("La suma es: {}", num1 + num2);
}
```

## Usando la Crate `clap`

Para un análisis más complejo de argumentos de línea de comando, la crate `clap` es una opción popular. Proporciona una forma declarativa de especificar argumentos, opciones y subcomandos.

### Ejemplo Básico con `clap`

Primero, agrega `clap` a tu `Cargo.toml`:

```toml
[dependencies]
clap = "4.0"
```

Aquí hay un ejemplo que usa `clap` para analizar un nombre y una edad opcional:

```rust
use clap::{Arg, Command};

fn main() {
    let matches = Command::new("mi_programa")
        .version("1.0")
        .author("Tu Nombre <tu.email@ejemplo.com>")
        .about("Programa de ejemplo con clap")
        .arg(Arg::new("nombre")
            .about("Establece el nombre a usar")
            .required(true)
            .index(1))
        .arg(Arg::new("edad")
            .about("Establece la edad a usar")
            .required(false)
            .index(2))
        .get_matches();

    let nombre = matches.value_of("nombre").unwrap();
    let edad = matches.value_of("edad").unwrap_or("desconocida");

    println!("Nombre: {}", nombre);
    println!("Edad: {}", edad);
}
```

Para ejecutar este programa:

```sh
cargo run -- Juan 30
```

Salida:

```
Nombre: Juan
Edad: 30
```

Si omites la edad:

```sh
cargo run -- Juan
```

Salida:

```
Nombre: Juan
Edad: desconocida
```

## Conclusión

Manejar argumentos de línea de comando en Rust puede ser tan simple o tan complejo como tu aplicación requiera. Para necesidades básicas, el módulo `std::env` es suficiente. Para escenarios más avanzados, la crate `clap` ofrece características extensas y facilidad de uso. Al aprovechar estas herramientas, puedes crear aplicaciones de línea de comando flexibles y amigables en Rust.