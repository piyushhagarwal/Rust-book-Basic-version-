# Introduction to Structs in Rust

Structs are a way to group related data together in Rust. They are similar to objects in other programming languages but do not include methods by default.

---

## Defining a Struct

A struct is defined using the `struct` keyword, followed by the struct name and its fields.

### Example: Defining a Struct

```rust
struct User {
    username: String,
    email: String,
    sign_in_count: u64,
    active: bool,
}
```

Here:

- `User` is the name of the struct.
- It has four fields: `username`, `email`, `sign_in_count`, and `active`.

---

## Creating an Instance

You can create an instance of a struct by specifying values for each field.

### Example: Creating a Struct Instance

```rust
fn main() {
    let user1 = User {
        username: String::from("rustacean"),
        email: String::from("rustacean@example.com"),
        sign_in_count: 1,
        active: true,
    };
}
```

---

## Accessing and Modifying Fields

You can access or modify fields of a struct using dot notation.

### Example: Accessing Fields

```rust
fn main() {
    let user1 = User {
        username: String::from("rustacean"),
        email: String::from("rustacean@example.com"),
        sign_in_count: 1,
        active: true,
    };

    println!("Username: {}", user1.username);
    println!("Email: {}", user1.email);
}
```

### Example: Modifying Fields

```rust
fn main() {
    let mut user1 = User {
        username: String::from("rustacean"),
        email: String::from("rustacean@example.com"),
        sign_in_count: 1,
        active: true,
    };

    user1.email = String::from("new_email@example.com");
    println!("Updated Email: {}", user1.email);
}
```

---

## Struct Update Syntax

Rust provides a shorthand for creating a new struct instance by copying some fields from an existing instance.

### Example: Struct Update Syntax

```rust
fn main() {
    let user1 = User {
        username: String::from("rustacean"),
        email: String::from("rustacean@example.com"),
        sign_in_count: 1,
        active: true,
    };

    let user2 = User {
        email: String::from("new_email@example.com"),
        ..user1
    };

    println!("User2 Email: {}", user2.email);
}
```

---

## Tuple Structs

Tuple structs are a lightweight version of structs, useful for grouping values without naming the fields.

### Example: Tuple Struct

```rust
struct Point(i32, i32);

fn main() {
    let p = Point(10, 20);
    println!("Point: ({}, {})", p.0, p.1);
}
```

---

## Unit-Like Structs

Unit-like structs do not have fields and are useful for implementing traits or as markers.

### Example: Unit-Like Struct

```rust
struct Marker;

fn main() {
    let _marker = Marker;
}
```

---

## Summary

Structs are fundamental in Rust for organizing and managing data. Key points:

- Use structs for named fields.
- Tuple structs for unnamed fields.
- Unit-like structs for markers or empty data types.

Next, we’ll explore **methods in structs**!
