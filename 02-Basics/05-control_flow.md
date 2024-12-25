# Control Flow in Rust

Control flow structures allow you to dictate how your program executes different blocks of code depending on conditions or iteration. Rust offers a variety of control flow constructs, including conditional statements, loops, and pattern matching.

---

## Conditional Statements: `if`, `else if`, `else`

### `if` Statement

Use the `if` statement to execute code based on a condition.

```rust
fn main() {
    let number = 5;

    if number > 0 {
        println!("The number is positive.");
    }
}
```

---

### `if` and `else`

Add an `else` block to handle cases where the condition is false.

```rust
fn main() {
    let number = -5;

    if number > 0 {
        println!("The number is positive.");
    } else {
        println!("The number is not positive.");
    }
}
```

---

### `else if`

Use `else if` to check multiple conditions in sequence.

```rust
fn main() {
    let number = 0;

    if number > 0 {
        println!("The number is positive.");
    } else if number < 0 {
        println!("The number is negative.");
    } else {
        println!("The number is zero.");
    }
}
```

---

### `if` as an Expression

In Rust, `if` can be used as an expression to return a value.

```rust
fn main() {
    let condition = true;
    let number = if condition { 5 } else { 10 };

    println!("The number is: {}", number);
}
```

---

## Loops in Rust

Rust provides three main types of loops: `loop`, `while`, and `for`.

### `loop`

The `loop` construct repeats indefinitely unless explicitly stopped.

```rust
fn main() {
    let mut count = 0;

    loop {
        count += 1;

        if count == 3 {
            println!("Count is 3, exiting the loop.");
            break;
        }
    }
}
```

---

### `while`

The `while` loop runs as long as a condition is true.

```rust
fn main() {
    let mut number = 3;

    while number > 0 {
        println!("{}", number);
        number -= 1;
    }

    println!("Liftoff!");
}
```

---

### `for`

The `for` loop is ideal for iterating over a range or a collection.

```rust
fn main() {
    for number in 1..4 {
        println!("{}", number);
    }

    println!("Liftoff!");
}
```

---

### Iterating Over a Collection

```rust
fn main() {
    let arr = [10, 20, 30, 40];

    for element in arr.iter() {
        println!("Element: {}", element);
    }
}
```

---

## Pattern Matching with `match`

The `match` construct allows for more expressive branching based on patterns.

### Example: `match` Control Flow

```rust
fn main() {
    let number = 1;

    match number {
        1 => println!("One"),
        2 => println!("Two"),
        _ => println!("Something else"),
    }
}
```

---

## `break` and `continue`

### `break`

Use `break` to exit a loop early.

```rust
fn main() {
    for number in 1..10 {
        if number == 5 {
            println!("Breaking out of the loop.");
            break;
        }
    }
}
```

---

### `continue`

Use `continue` to skip to the next iteration of a loop.

```rust
fn main() {
    for number in 1..10 {
        if number % 2 == 0 {
            continue; // Skip even numbers
        }

        println!("Odd number: {}", number);
    }
}
```

---

## Returning Values from Loops

The `loop` construct can return a value using `break`.

```rust
fn main() {
    let mut counter = 0;

    let result = loop {
        counter += 1;

        if counter == 10 {
            break counter * 2;
        }
    };

    println!("The result is: {}", result);
}
```

---

## Summary

Rust's control flow features provide powerful tools to manage the execution of your programs:

- Conditional branches with `if`, `else if`, and `else`.
- Looping constructs: `loop`, `while`, and `for`.
- Pattern matching with `match`.
- Loop control with `break` and `continue`.

These constructs allow you to write expressive, efficient, and readable code. Next, we'll explore **error handling and the `Result` type in Rust**!
