# Appendix

## [Appendix A: Keywords](https://rust-book.cs.brown.edu/appendix-01-keywords.html#appendix-a-keywords)

Keywords are reserved words specific to the Rust programming language. They cannot be used as identifiers (except as raw identifiers). Identifiers are names of functions, variables, parameters, struct fields, modules, crates, constants, macros, static values, attributes, types, traits, or lifetimes.

### Keywords Currently in Use

The following is a list of keywords currently in use, with their functionality described.

- `as` - perform primitive casting, disambiguate the specific trait containing an item, or rename items in use statements
- `async` - return a Future instead of blocking the current thread
- `await` - suspend execution until the result of a Future is ready
- `break` - exit a loop immediately
- `const` - define constant items or constant raw pointers
- `continue` - continue to the next loop iteration
- `crate` - in a module path, refers to the crate root
- `dyn` - dynamic dispatch to a trait object
- `else` - fallback for if and if let control flow constructs
- `enum` - define an enumeration
- `extern` - link an external function or variable
- `false` - Boolean false literal
- `fn` - define a function or the function pointer type
- `for` - loop over items from an iterator, implement a trait, or specify a higher-ranked lifetime
- `if` - branch based on the result of a conditional expression
- `impl` - implement inherent or trait functionality
- `in` - part of for loop syntax
- `let` - bind a variable
- `loop` - loop unconditionally
- `match` - match a value to patterns
- `mod` - define a module
- `move` - make a closure take ownership of all its captures
- `mut` - denote mutability in references, raw pointers, or pattern bindings
- `pub` - denote public visibility in struct fields, impl blocks, or modules
- `ref` - bind by reference
- `return` - return from function
- `Self` - a type alias for the type we are defining or implementing
- `self` - method subject or current module
- `static` - global variable or lifetime lasting the entire program execution
- `struct` - define a structure
- `super` - parent module of the current module
- `trait` - define a trait
- `true` - Boolean true literal
- `type` - define a type alias or associated type
- `union` - define a union; is only a keyword when used in a union declaration
- `unsafe` - denote unsafe code, functions, traits, or implementations
- `use` - bring symbols into scope
- `where` - denote clauses that constrain a type
- `while` - loop conditionally based on the result of an expression

### Keywords Reserved for Future Use

The following keywords do not yet have any functionality but are reserved by Rust for potential future use.

- `abstract`
- `become`
- `box`
- `do`
- `final`
- `macro`
- `override`
- `priv`
- `try`
- `typeof`
- `unsized`
- `virtual`
- `yield`

### Raw Identifiers

_Raw identifiers_ allow you to escape reserved keywords. You can create a raw identifier by prefixing a keyword with `r#`.

Raw identifiers allow you to...

- More easy integrate with other programming languages
- Use multiple Rust editions, as reserved keywords may not have existed in older editions

#### Example

This code will not compile:

```rust
fn match(needle: &str, haystack: &str) -> bool {
    haystack.contains(needle)
}
```

Adding a raw identifier to the name of the function will allow it to compile:

```rust
fn r#match(needle: &str, haystack: &str) -> bool {
    haystack.contains(needle)
}
```

## [Appendix B: Operators and Symbols](https://rust-book.cs.brown.edu/appendix-02-operators.html#appendix-b-operators-and-symbols)

## [Appendix C: Derivable Traits](https://rust-book.cs.brown.edu/appendix-03-derivable-traits.html#appendix-c-derivable-traits)

## [Appendix D: Useful Development Tools](https://rust-book.cs.brown.edu/appendix-04-useful-development-tools.html#appendix-d---useful-development-tools)

### Automatic Formatting with `rustfmt`

The `rustfmt` tool reformats your code according to the community code style.

To install:

```sh
rustup component add rustfmt
```

To format and Cargo project:

```sh
cargo fmt
```

### Fix Your Code with `rustfix`

`rustfix` is included with Rust and will autocorrect common compiler warnings.

### More Lints with Clippy

The Clippy tool is a collection of lints to analyze your code so you can catch common mistakes and improve your Rust code.

To install:

```sh
rustup component add clippy
```

To run Clippy's lints  on any Cargo project:

```sh
cargo clippy
```

### IDE Integration Using `rust-analyzer`

Different clients can use rust-analyzer, such as [the Rust analyzer plug-in for Visual Studio Code](https://marketplace.visualstudio.com/items?itemName=rust-lang.rust-analyzer).

Visit the rust-analyzer project’s [home page](https://rust-analyzer.github.io/) for installation instructions, then install the language server support in your particular IDE. Your IDE will gain abilities such as autocompletion, jump to definition, and inline errors.

## [Appendix E: Editions](https://rust-book.cs.brown.edu/appendix-05-editions.html#appendix-e---editions)

The Rust language and compiler have a six-week release cycle, but every two to three years, the Rust team produces a new Rust _edition_.

There are currently three Rust editions: Rust 2015, Rust 2018, and Rust 2021.

The `edition` key in _Cargo.toml_ tells the compiler which edition to use for your code. If there's no value, it defaults to `2015` to ensure backwards compatibility.

The [_Edition Guide_](https://doc.rust-lang.org/stable/edition-guide/) explains the differences between editions and walks users through upgrades using `cargo fix`.

## [Appendix G: How Rust Is Made and "Nightly Rust"](https://rust-book.cs.brown.edu/appendix-07-nightly-rust.html#appendix-g---how-rust-is-made-and-nightly-rust)

### Stability Without Stagnation

Our guiding principle is this: you should never have to fear upgrading to a new version of stable Rust. Each upgrade should be painless, but should also bring you new features, fewer bugs, and faster compile times.

### Release Channels and Riding the Trains

Rust has three release channels: Nightly, Beta, and Stable.

This is called the “train model” because every six weeks, a release “leaves the station” (nightly), but still has to take a journey through the beta channel before it arrives as a stable release.

### Unstable Features

All unstable features are located on the nightly release hidden behind feature flags. You can test them out, but you have to opt in with the appropriate flag.

### The RFC Process and Teams

Rust's development model follows a _Request For Comments (RFC) process_. If you'd like an improvement in Rust, you can write up a proposal, called an RFC.
