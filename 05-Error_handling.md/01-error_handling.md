# Error Handling in Rust

Error handling in Rust is designed to be robust and safe, encouraging developers to handle errors explicitly. Rust offers two main ways to deal with errors:

1. **Recoverable errors** using the `Result` type.
2. **Unrecoverable errors** using the `panic!` macro.

---

## Unrecoverable Errors with `panic!`

The `panic!` macro stops the program execution and prints an error message.

### Example: Using `panic!`

```rust
fn main() {
    panic!("Something went wrong!");
}
```

When `panic!` is called:

- The program prints a message.
- It unwinds the stack by default, cleaning up resources.

### Configuring `panic` Behavior

Rust can either **unwind** the stack or **abort** the program. You can configure this behavior in `Cargo.toml`:

```toml
[profile.release]
panic = "abort"
```

---

## Recoverable Errors with `Result`

Rust uses the `Result` enum to handle recoverable errors. The `Result` type is defined as:

```rust
enum Result<T, E> {
    Ok(T), // Contains the successful value
    Err(E), // Contains the error value
}
```

### Example: Basic `Result` Usage

```rust
use std::fs::File;

fn main() {
    let file_result = File::open("nonexistent_file.txt");

    match file_result {
        Ok(file) => println!("File opened successfully: {:?}", file),
        Err(error) => println!("Failed to open the file: {:?}", error),
    }
}
```

---

## Propagating Errors with `?`

The `?` operator simplifies error propagation. It returns the error to the calling function if an operation fails.

### Example: Propagating Errors

```rust
use std::fs::File;
use std::io::{self, Read};

fn read_file_content(path: &str) -> Result<String, io::Error> {
    let mut file = File::open(path)?; // Propagate error if `File::open` fails
    let mut content = String::new();
    file.read_to_string(&mut content)?;
    Ok(content)
}

fn main() {
    match read_file_content("example.txt") {
        Ok(content) => println!("File content: {}", content),
        Err(error) => println!("Error reading file: {:?}", error),
    }
}
```

---

## The `unwrap` and `expect` Methods

### `unwrap`

The `unwrap` method extracts the value inside `Ok`, or panics if it's an `Err`.

```rust
use std::fs::File;

fn main() {
    let file = File::open("example.txt").unwrap();
    println!("File opened successfully: {:?}", file);
}
```

### `expect`

The `expect` method is similar to `unwrap` but allows you to provide a custom error message.

```rust
use std::fs::File;

fn main() {
    let file = File::open("example.txt").expect("Failed to open the file");
    println!("File opened successfully: {:?}", file);
}
```

> **Note:** Avoid using `unwrap` or `expect` in production code unless you're certain the operation will succeed.

---

## Custom Error Types

Rust allows you to define custom error types for more expressive error handling.

### Example: Custom Error Type

```rust
use std::fmt;

#[derive(Debug)]
enum MyError {
    IoError(std::io::Error),
    ParseError(std::num::ParseIntError),
}

impl fmt::Display for MyError {
    fn fmt(&self, f: &mut fmt::Formatter<'_>) -> fmt::Result {
        match self {
            MyError::IoError(e) => write!(f, "IO error: {}", e),
            MyError::ParseError(e) => write!(f, "Parse error: {}", e),
        }
    }
}

fn main() {
    let result: Result<(), MyError> = Err(MyError::IoError(std::io::Error::new(
        std::io::ErrorKind::NotFound,
        "File not found",
    )));

    match result {
        Ok(_) => println!("Operation succeeded."),
        Err(e) => println!("Error: {}", e),
    }
}
```

---

## Using `Result` with `match` vs `?`

### Using `match`

```rust
use std::fs::File;

fn main() {
    let file_result = File::open("example.txt");

    match file_result {
        Ok(file) => println!("File opened successfully: {:?}", file),
        Err(error) => println!("Error: {:?}", error),
    }
}
```

### Using `?`

```rust
use std::fs::File;

fn main() -> Result<(), std::io::Error> {
    let file = File::open("example.txt")?;
    println!("File opened successfully: {:?}", file);
    Ok(())
}
```

---

## Combining Multiple Errors with `thiserror`

For larger projects, crates like `thiserror` simplify custom error handling.

### Example: Using `thiserror`

Add the crate to `Cargo.toml`:

```toml
[dependencies]
thiserror = "1.0"
```

Define a custom error type:

```rust
use thiserror::Error;

#[derive(Error, Debug)]
enum MyError {
    #[error("IO error occurred: {0}")]
    Io(#[from] std::io::Error),

    #[error("Parsing error occurred: {0}")]
    Parse(#[from] std::num::ParseIntError),
}

fn main() -> Result<(), MyError> {
    let number: i32 = "abc".parse()?;
    Ok(())
}
```

---

## Summary

Rust's error handling encourages:

- **Explicitness** through the `Result` type.
- **Robustness** with tools like `?`, `unwrap`, `expect`, and custom error types.
- **Flexibility** via libraries like `thiserror` for more complex scenarios.

By using these tools effectively, you can write safe and predictable Rust programs.

Next, we'll explore **ownership and borrowing**, a core concept in Rust for memory safety!
