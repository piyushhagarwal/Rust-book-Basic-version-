# Methods in Structs

In Rust, you can define methods for structs to associate functionality with the struct. Methods are defined using `impl` blocks.

---

## Defining Methods

Methods take `self` as their first parameter and are defined within an `impl` block.

### Example: Method in a Struct

```rust
struct Rectangle {
    width: u32,
    height: u32,
}

impl Rectangle {
    fn area(&self) -> u32 {
        self.width * self.height
    }
}

fn main() {
    let rect = Rectangle {
        width: 10,
        height: 20,
    };

    println!("Area: {}", rect.area());
}
```

---

## Associated Functions

Associated functions do not take `self` as a parameter. They are often used as constructors.

### Example: Associated Function

```rust
struct Rectangle {
    width: u32,
    height: u32,
}

impl Rectangle {
    fn square(size: u32) -> Rectangle {
        Rectangle {
            width: size,
            height: size,
        }
    }
}

fn main() {
    let square = Rectangle::square(10);
    println!("Square dimensions: {} x {}", square.width, square.height);
}
```

---

## Multiple `impl` Blocks

You can define multiple `impl` blocks for a struct.

### Example: Multiple `impl` Blocks

```rust
struct Rectangle {
    width: u32,
    height: u32,
}

impl Rectangle {
    fn area(&self) -> u32 {
        self.width * self.height
    }
}

impl Rectangle {
    fn perimeter(&self) -> u32 {
        2 * (self.width + self.height)
    }
}

fn main() {
    let rect = Rectangle {
        width: 10,
        height: 20,
    };

    println!("Area: {}", rect.area());
    println!("Perimeter: {}", rect.perimeter());
}
```

---

## Summary

Methods in structs allow encapsulating functionality within the struct itself. You can:

- Define methods with `self`.
- Use associated functions as constructors.
- Use multiple `impl` blocks for better organization.

Next, we’ll dive into **Enums in Rust**!
