# Introduction to Enums in Rust

Enums allow you to define a type that can have multiple possible values. Each value can optionally hold data. Enums are a versatile way to represent data that can vary.

---

## Defining an Enum

Enums are defined using the `enum` keyword.

### Example: Basic Enum

```rust
enum Direction {
    North,
    South,
    East,
    West,
}

fn main() {
    let dir = Direction::North;
    match dir {
        Direction::North => println!("Going North!"),
        Direction::South => println!("Going South!"),
        Direction::East => println!("Going East!"),
        Direction::West => println!("Going West!"),
    }
}
```

---

## Enums with Data

Enums can store data within their variants.

### Example: Enum with Data

```rust
enum Message {
    Quit,
    Move { x: i32, y: i32 },
    Write(String),
    ChangeColor(i32, i32, i32),
}

fn main() {
    let msg = Message::Move { x: 10, y: 20 };

    match msg {
        Message::Quit => println!("Quit"),
        Message::Move { x, y } => println!("Move to ({}, {})", x, y),
        Message::Write(text) => println!("Write: {}", text),
        Message::ChangeColor(r, g, b) => println!("Change color to ({}, {}, {})", r, g, b),
    }
}
```

---

## Using `impl` with Enums

You can define methods for enums using `impl`.

### Example: Methods in Enums

```rust
enum Message {
    Write(String),
}

impl Message {
    fn call(&self) {
        match self {
            Message::Write(text) => println!("Message: {}", text),
        }
    }
}

fn main() {
    let msg = Message::Write(String::from("Hello, Rust!"));
    msg.call();
}
```

---

## Summary

Enums are a powerful tool in Rust:

- Represent multiple possible values.
- Store data within variants.
- Extend functionality with methods.
