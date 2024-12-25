# Ownership in Rust

Ownership is one of the most unique and powerful features of Rust. It enables Rust to manage memory safety without needing a garbage collector. In this chapter, we’ll explore what ownership is, how it works, and the rules that govern it.

## What is Ownership?

Ownership refers to the system by which Rust ensures that only one piece of code has control over a value at any given time. When the owner goes out of scope, the value is automatically cleaned up.

### Ownership Rules

1. Each value in Rust has a variable that’s called its owner.
2. There can be only one owner at a time.
3. When the owner goes out of scope, the value is dropped.

### Example

```rust
fn main() {
    let s = String::from("Hello, Rust!");  // `s` is the owner of the String
    println!("{}", s);  // Valid because `s` is still in scope
}  // `s` goes out of scope and the memory is automatically freed
```

In this example, the `String` value is dropped when it goes out of scope at the end of `main`.

---

## Move Semantics

When you assign one variable to another, the ownership is **moved**. This means the original owner is no longer valid.

```rust
fn main() {
    let s1 = String::from("Hello");
    let s2 = s1;  // Ownership of `s1` is moved to `s2`

    // println!("{}", s1);  // Error: `s1` is no longer valid
    println!("{}", s2);  // Valid because `s2` now owns the value
}
```

When `s1` is moved to `s2`, `s1` can no longer be used. This prevents double free errors.

---

## Borrowing and References

If you want to let another variable access a value without transferring ownership, you can **borrow** it using references (`&`).

### Immutable Borrowing

You can create multiple immutable references, but you cannot modify the value.

```rust
fn main() {
    let s = String::from("Hello");

    let r1 = &s;  // Immutable reference
    let r2 = &s;  // Another immutable reference

    println!("{} and {}", r1, r2);  // Both references are valid
}
```

### Mutable Borrowing

You can create a mutable reference to modify the value, but only one mutable reference is allowed at a time to avoid data races.

```rust
fn main() {
    let mut s = String::from("Hello");

    let r = &mut s;  // Mutable reference
    r.push_str(", Rust!");

    println!("{}", r);  // Modified value
}
```

### Mutable and Immutable References Together

Rust enforces that you cannot mix mutable and immutable references in the same scope.

```rust
fn main() {
    let mut s = String::from("Hello");

    let r1 = &s;  // Immutable reference
    // let r2 = &mut s;  // Error: Cannot borrow `s` as mutable while it's immutably borrowed
}
```

---

## The `Clone` Trait

If you want to create a deep copy of a value, you can use the `.clone()` method.

```rust
fn main() {
    let s1 = String::from("Hello");
    let s2 = s1.clone();  // Creates a deep copy of `s1`

    println!("s1: {}, s2: {}", s1, s2);  // Both are valid
}
```

---

## Ownership and Functions

When a value is passed to a function, ownership is transferred to the function unless you use references.

### Transferring Ownership

```rust
fn take_ownership(s: String) {
    println!("{}", s);
}  // `s` is dropped here

fn main() {
    let s = String::from("Hello");
    take_ownership(s);  // Ownership is transferred to the function

    // println!("{}", s);  // Error: `s` is no longer valid
}
```

### Borrowing with Functions

You can pass a reference to avoid transferring ownership.

```rust
fn borrow_value(s: &String) {
    println!("{}", s);  // Only borrows, does not take ownership
}

fn main() {
    let s = String::from("Hello");
    borrow_value(&s);  // Passing a reference
    println!("{}", s);  // Still valid
}
```

---

## The `Copy` Trait

Some types, like integers, implement the `Copy` trait, meaning their values are copied rather than moved. You can use these types without worrying about ownership.

```rust
fn main() {
    let x = 5;  // `x` is of type i32, which implements `Copy`
    let y = x;  // `x` is copied to `y`

    println!("x: {}, y: {}", x, y);  // Both are valid
}
```

Types like `String` do not implement `Copy` because they manage heap memory.

---

## Dangling References

Rust prevents dangling references at compile time. A dangling reference occurs when a reference points to memory that has already been freed.

### Example: Dangling Reference Prevention

```rust
fn main() {
    let r;
    {
        let s = String::from("Rust");
        r = &s;  // Error: `s` does not live long enough
    }
    // println!("{}", r);  // `s` is dropped here
}
```

In this example, `s` is dropped when the inner block ends. Rust’s borrow checker ensures that `r` cannot outlive `s`.

---

## Slices: A Special Kind of Borrowing

Slices are a way to borrow a part of a collection, such as a portion of a `String` or an array.

### Example: String Slices

```rust
fn main() {
    let s = String::from("Hello, Rust!");
    let hello = &s[0..5];  // Borrowing a slice
    let rust = &s[7..11];  // Borrowing another slice

    println!("{} {}", hello, rust);  // Prints: Hello Rust
}
```

Slices are references, so they do not take ownership.

## Conclusion

In this chapter, we covered:

- The ownership model and its rules.
- Move semantics and how ownership transfers.
- Borrowing with references, both immutable and mutable.
- Using the `Clone` trait for deep copies.
- Differences between types that implement `Copy` and those that don’t.
- Preventing dangling references with Rust’s borrow checker.
- Slices as a special kind of borrowing.

Ownership is a foundational concept in Rust. Mastering it will help you write memory-safe and efficient code. In the next chapter, we’ll discuss **Borrowing and Lifetimes**, which build on these concepts.

---
