# Pattern Matching with Enums

Pattern matching is one of Rust's most powerful features, and it works seamlessly with enums. Using the `match` expression, you can handle all possible variants of an enum in a clear and concise way.

---

## Basic Pattern Matching with Enums

You can use the `match` expression to handle each variant of an enum.

### Example: Matching Enum Variants

```rust
enum Direction {
    North,
    South,
    East,
    West,
}

fn main() {
    let direction = Direction::East;

    match direction {
        Direction::North => println!("Heading North!"),
        Direction::South => println!("Heading South!"),
        Direction::East => println!("Heading East!"),
        Direction::West => println!("Heading West!"),
    }
}
```

---

## Matching Enums with Data

When an enum variant holds data, you can destructure it inside the `match` expression.

### Example: Matching Enums with Data

```rust
enum Message {
    Quit,
    Move { x: i32, y: i32 },
    Write(String),
    ChangeColor(i32, i32, i32),
}

fn main() {
    let message = Message::Move { x: 15, y: 25 };

    match message {
        Message::Quit => println!("The program will quit."),
        Message::Move { x, y } => println!("Moving to coordinates ({}, {})", x, y),
        Message::Write(text) => println!("Message: {}", text),
        Message::ChangeColor(r, g, b) => println!("Changing color to RGB({}, {}, {})", r, g, b),
    }
}
```

---

## Using `if let` for Simplified Matching

For cases where you care about only one variant, you can use `if let` instead of a full `match`.

### Example: Using `if let`

```rust
enum Message {
    Quit,
    Write(String),
}

fn main() {
    let msg = Message::Write(String::from("Hello, Rust!"));

    if let Message::Write(text) = msg {
        println!("Message: {}", text);
    }
}
```

---

## Combining Patterns with `match`

Rust allows combining patterns to handle multiple variants in a single arm.

### Example: Combining Patterns

```rust
enum Direction {
    North,
    South,
    East,
    West,
}

fn main() {
    let direction = Direction::East;

    match direction {
        Direction::North | Direction::South => println!("Heading vertically."),
        Direction::East | Direction::West => println!("Heading horizontally."),
    }
}
```

---

## Using `_` to Handle Remaining Cases

The `_` pattern matches any value and is often used as a fallback.

### Example: Default Case with `_`

```rust
enum Direction {
    North,
    South,
    East,
    West,
}

fn main() {
    let direction = Direction::North;

    match direction {
        Direction::North => println!("Going North!"),
        _ => println!("Not heading North."),
    }
}
```

---

## Nested Pattern Matching

For enums with complex data, you can use nested patterns.

### Example: Nested Pattern Matching

```rust
enum Message {
    Move { x: i32, y: i32 },
    ChangeColor(i32, i32, i32),
}

fn main() {
    let msg = Message::Move { x: 10, y: 20 };

    match msg {
        Message::Move { x, y } if x > 0 => println!("Moving to positive x: {}, y: {}", x, y),
        Message::Move { x, y } => println!("Moving to x: {}, y: {}", x, y),
        Message::ChangeColor(r, g, b) => println!("Changing color to ({}, {}, {})", r, g, b),
    }
}
```

---

## Summary

Pattern matching is an essential feature in Rust, allowing you to:

- Handle each enum variant clearly with `match`.
- Destructure enum variants to extract data.
- Use `if let` for concise matching.
- Combine patterns and use `_` for default cases.

With pattern matching, you can write expressive and safe code for handling enums. In the next section, we’ll explore **error handling with enums**!
