# Variables and Mutability in Rust

In this chapter, we will explore variables and their mutability in Rust. Rust's approach to variables ensures memory safety while providing the flexibility needed for efficient programming.

## Immutable Variables

By default, variables in Rust are **immutable**. This means once a value is assigned to a variable, it cannot be changed. This is a key part of Rust's safety guarantees, as it prevents accidental changes to values.

```rust
fn main() {
    let x = 5;  // Immutable variable
    // x = 10;  // This will cause an error because x is immutable
    println!("The value of x is: {}", x);
}
```

Attempting to change the value of `x` results in a compile-time error.

## Mutable Variables

To make a variable mutable, we need to explicitly declare it with the `mut` keyword. Once a variable is mutable, its value can be changed during execution.

```rust
fn main() {
    let mut y = 10;  // Mutable variable
    y = 20;  // This is allowed because y is mutable
    println!("The value of y is: {}", y);
}
```

### Key Points:

- **`let`**: Used to declare a variable.
- **`mut`**: Makes a variable mutable.

## Shadowing

Rust also supports **shadowing**, which allows you to reuse the same variable name. When you shadow a variable, the original variable is replaced by a new one. This can be useful in certain cases, such as when you need to change the type of a variable.

```rust
fn main() {
    let x = 5;  // Immutable variable
    let x = x + 1;  // Shadowing the original variable
    let x = x * 2;  // Shadowing again

    println!("The value of x is: {}", x);  // 12
}
```

In the example above, the original value of `x` is not modified directly. Instead, a new variable `x` is created each time we shadow it. This allows us to modify the value while keeping the original one intact.

## Constants

In addition to variables, Rust also provides **constants**. Constants are always immutable and must have their type explicitly specified. They are not bound by the scope of a function and can be used throughout the program.

```rust
const MAX_POINTS: u32 = 100_000;  // Constant variable
```

Constants can be declared at the global scope (outside of functions) or inside functions, but they must be assigned a value at the time of declaration.

## Conclusion

In this chapter, we learned about:

- **Immutable variables**: Default behavior in Rust.
- **Mutable variables**: Using the `mut` keyword.
- **Shadowing**: Reusing variable names with new values.
- **Constants**: Declaring global, immutable values.

In the next chapter, we’ll dive into **Data Types** in Rust.

---

This concludes our exploration of variables and mutability in Rust. Let’s continue with **Data Types** in the next chapter!
