# Rust Syntax Overview

Rust's syntax is designed to be clean, expressive, and easy to read. In this chapter, we’ll take a look at the basic syntax of Rust programs, including how to structure your code, write functions, and work with common programming constructs.

## A Simple Rust Program

Let’s start by writing a simple Rust program that prints a message to the screen:

```rust
fn main() {
    println!("Hello, world!");
}
```

### Breakdown:

- **`fn main()`**: The entry point of a Rust program. The `main` function is always executed first when you run a Rust program.
- **`println!`**: This is a macro in Rust (indicated by the `!`), which prints a string to the console.

### Rust Program Structure

A Rust program is divided into functions. The `main` function is special, but you can define your own functions as well. Here's an example of a function:

```rust
fn greet(name: &str) {
    println!("Hello, {}!", name);
}

fn main() {
    greet("Rust");
}
```

### Key Points:

- **Functions**: Defined with the `fn` keyword.
- **Parameters**: The `greet` function takes a parameter called `name`, which is a string slice (`&str`).
- **Return Types**: Functions in Rust can return values. The return type is specified after `->`, e.g., `fn add(a: i32, b: i32) -> i32`.

## Comments

Rust supports both single-line and multi-line comments:

```rust
// This is a single-line comment

/*
  This is a
  multi-line comment
*/
```

## Variables and Constants

In Rust, variables are immutable by default, meaning once they are assigned a value, it cannot be changed. However, you can make them mutable by using the `mut` keyword.

```rust
fn main() {
    let x = 5;  // Immutable variable
    let mut y = 10;  // Mutable variable

    y = 20;  // This is allowed because `y` is mutable

    println!("x: {}, y: {}", x, y);
}
```

- **`let`**: Used to declare variables.
- **`mut`**: Makes the variable mutable.

Constants are declared with the `const` keyword and must have their type specified:

```rust
const MAX_POINTS: u32 = 100_000;
```

## Conclusion

In this chapter, we covered the basic structure of a Rust program, how to write functions, and the use of variables and constants. Next, we'll explore more advanced concepts like data types and control flow.

---

This concludes the introduction to Rust syntax. Let’s continue with the next chapter on **Variables and Mutability**!
