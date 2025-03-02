---
minutes: 2
---

# Macros

Macros are expanded into Rust code during compilation, and can take a variable
number of arguments. They are distinguished by a `!` at the end. The Rust
standard library includes an assortment of useful macros.

- `println!(format, ..)` prints a line to standard output, applying formatting
  described in [`std::fmt`](https://doc.rust-lang.org/std/fmt/index.html).
- `format!(format, ..)` works just like `println!` but returns the result as a
  string.
- `dbg!(expression)` logs the value of the expression and returns it.
- `todo!()` marks a bit of code as not-yet-implemented. If executed, it will
  panic.

```rust,editable
fn factorial(n: u32) -> u32 {
    let mut product = 1;
    for i in 1..=n {
        product *= dbg!(i);
    }
    product
}

fn fizzbuzz(n: u32) -> u32 {
    todo!()
}

fn main() {
    let n = 4;
    println!("{n}! = {}", factorial(n));
}
```

<details>

The takeaway from this section is that these common conveniences exist, and how
to use them. Why they are defined as macros, and what they expand to, is not
especially critical.

The course does not cover defining macros, but a later section will describe use
of derive macros.

## More To Explore

There are a number of other useful macros provided by the standard library. Some
other examples you can share with students if they want to know more:

- [`assert!`] and related macros can be used to add assertions to your code.
  These are used heavily in writing tests.
- [`unreachable!`] is used to mark a branch of control flow that should never be
  hit.
- [`eprintln!`] allows you to print to stderr.

</details>

[`assert!`]: https://doc.rust-lang.org/stable/std/macro.assert.html
[`unreachable!`]: https://doc.rust-lang.org/stable/std/macro.unreachable.html
[`eprintln!`]: https://doc.rust-lang.org/stable/std/macro.eprintln.html
