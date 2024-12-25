# Data Types in Rust

Rust is a statically typed language, meaning that the type of every variable is known at compile time. This allows Rust to catch many errors early in the development process. In this chapter, we will explore the most common data types in Rust.

## Scalar Types

Scalar types represent a single value. Rust has four primary scalar types: integers, floating-point numbers, booleans, and characters.

### Integer Types

Rust provides several integer types, both signed and unsigned. They differ in size and whether they can represent negative values.

- **Signed integers**: Can store both positive and negative numbers.
- **Unsigned integers**: Can only store positive numbers (and zero).

Here are the common integer types in Rust:

- **`i8`, `i16`, `i32`, `i64`, `i128`**: Signed integers of various sizes (8, 16, 32, 64, 128 bits).
- **`u8`, `u16`, `u32`, `u64`, `u128`**: Unsigned integers of various sizes (8, 16, 32, 64, 128 bits).

```rust
fn main() {
    let x: i32 = -5;  // Signed 32-bit integer
    let y: u32 = 10;   // Unsigned 32-bit integer

    println!("x: {}, y: {}", x, y);
}
```

You can also use the `isize` and `usize` types, which depend on the architecture (32-bit or 64-bit).

### Floating-Point Types

Rust has two floating-point types, both of which are represented as 64-bit values:

- **`f32`**: 32-bit floating point
- **`f64`**: 64-bit floating point (default type)

```rust
fn main() {
    let x: f32 = 3.14;
    let y: f64 = 2.718;

    println!("x: {}, y: {}", x, y);
}
```

### Boolean Type

The `bool` type is used to represent true/false values.

```rust
fn main() {
    let is_rust_fun: bool = true;
    let is_easy: bool = false;

    println!("Is Rust fun? {}", is_rust_fun);
    println!("Is Rust easy? {}", is_easy);
}
```

### Character Type

Rust’s `char` type represents a single Unicode character.

```rust
fn main() {
    let letter: char = 'A';  // Single character
    let emoji: char = '😊';  // Unicode character

    println!("Letter: {}, Emoji: {}", letter, emoji);
}
```

## Compound Types

In addition to scalar types, Rust has compound types, which can group multiple values into a single type. Rust’s two compound types are tuples and arrays.

### Tuples

A tuple is a collection of values of different types. Tuples have a fixed length, and you can access the values by index.

```rust
fn main() {
    let person: (&str, u32) = ("Alice", 30);

    println!("Name: {}, Age: {}", person.0, person.1);
}
```

### Arrays

An array is a collection of values of the same type with a fixed size. Arrays are useful when you need to work with a fixed number of elements.

```rust
fn main() {
    let numbers: [i32; 3] = [1, 2, 3];

    println!("First number: {}", numbers[0]);
    println!("Second number: {}", numbers[1]);
    println!("Third number: {}", numbers[2]);
}
```

Arrays have a fixed size, which is part of their definition. If you need a collection with a dynamically changing size, you’ll want to use **Vectors** (covered later in the book).

## Type Inference

Rust is smart enough to infer the types of variables in many cases, meaning you don’t always have to specify the type explicitly. The following code will work even though we haven’t specified types:

```rust
fn main() {
    let x = 5;  // Rust infers that x is an i32
    let y = 3.14;  // Rust infers that y is an f64

    println!("x: {}, y: {}", x, y);
}
```

However, it’s often a good practice to explicitly define types for clarity and to avoid errors.

## Conclusion

In this chapter, we learned about:

- **Scalar types**: integers, floating-point numbers, booleans, and characters.
- **Compound types**: tuples and arrays.
- **Type inference**: Rust’s ability to automatically infer types.

In the next chapter, we’ll look at **Functions** and how to define and use them in Rust.

---

This concludes the overview of data types in Rust. Let’s move on to **Functions** in the next chapter!
