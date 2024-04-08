# 1. Getting Started

## 1.1. Installation

Download Rust with `rustup`, a command line tool for managing Rust versions and associated tools.

Install `rustup` by running the following command in your terminal:

```sh
curl --proto '=https' --tlsv1.2 https://sh.rustup.rs -sSf | sh
```

You will also need a _linker_, a program that Rust uses to join its compiled outputs into one file. C compilers typically include a linker and, luckily, you can get a C compiler on macOS by running:

```sh
xcode-select --install
```

Check whether you have Rust installed correctly. Completely close out your terminal, then open a new one and enter this line:

```sh
rustc --version
```

If you see the following, you have installed rust successfully:

```sh
rustc x.y.z (abcabcabc yyyy-mm-dd)
```

The format above is version number, commit hash, and commit date for the latest stable version that has been released.

### Updating and Uninstalling

Update to a new release version by running:

```sh
rustup update
```

To uninstall Rust and `rustup`:

```sh
rustup self uninstall
```

### Local Documentation

Rust also includes a local copy of the documentation – no Internet needed! All you have to do is run `rustup doc` and it will open in your browser.

## 1.2. Hello, World!

Let's make a "Hello, World!" app.

### Writing and Running a Rust Program

Create a new directory to hold your project. Then make a new source file titled _main.rs_. Rust files always end in the _.rs_ extension and use snake case for multiword filenames (i.e., _hello\_world.rs_).

Write the following code in the _main.rs_ file:

```rs
fn main() {
    println!("Hello, world!");
}
```

After saving the file, navigate to the project's home directory in your terminal. Enter the following commands to compile and run _main.rs_:

```sh
rustc main.rs
./main
```

You should see the string `"Hello, world!"` print out to your terminal.

### Anatomy of a Rust Program

```rs
fn main() {

}
```

The lines above define a function named `main`. The `main` function is special: it's always the first code that runs in every executable Rust program. This function has no parameters, as we can tell from the empty parentheses (`()`), and returns nothing.

Rust requires that all function bodies be wrapped in curly braces (`{}`). The opening curly bracket (`{`) should follow the function declaration by one whitespace.

The body of the `main` function contains the line:

```rs
    println!("Hello, world!");
```

Which prints text to the screen. Some details...

- Rust indents with four spaces.
- `println!` calls a Rust macro. Using the exclamation point (`!`) means that you're calling a macro instead of a normal function and macros don't always follow the same rules as functions
- The line ends with a semicolon (`;`) to indicate that the expression is over and the next one is ready to begin. Most lines of Rust code end with a semicolon.

### Compiling and Running Are Separate Steps

Before running a Rust program, it needs to be compiled using the Rust compiler. To do this, enter the `rustc` command and pass it the name of your source file. For example:

```rs
rustc main.rs
```

After compiling, Rust puts out a binary executable. Now you'll see two files in your project folder: `main.rs` and `main`.

Now you just run the file like so:

```sh
./main
```

Rust is an _ahead-of-time compiled_ language, unlike Ruby, Python, or JavaScript. This means you can compile a program and give the executable to someone else with a matching OS who can then run it even without having Rust installed! With _.rb_, _.py_, and _.js_ files, they need to have Ruby, Python, and JavaScript installed. In turn, they only need one command to compile and run the program.

## 1.3. Hello, Cargo!

Cargo is Rust's build system and package manager.

Check whether Cargo is installed by entering the following into your terminal:

```sh
cargo --version
```

### Creating a Project with Cargo

To create a new project with Cargo, start in your home directory and run:

```sh
cargo new hello_cargo
cd hello_cargo
```

The first command creates a new directory called _hello\_cargo_ and places the project files inside that directory. The second command changes us to the _hello\_cargo_ directory.

Nested inside we find a _Cargo.toml_ file and an _src_ directory containing a file called _main.rs_. It has also included a _.gitignore_ file and initialize a new Git repository.

_Cargo.toml_ should look like:

```toml
[package]
name = "hello_cargo"
version = "0.1.0"
edition = "2021"

# See more keys and their definitions at https://doc.rust-lang.org/cargo/reference/manifest.html

[dependencies]
```

This file is in the [_TOML (Tom’s Obvious, Minimal Language)_](https://toml.io/) format, which is Cargo’s configuration format.

The `[section]` format signifies a configuration section heading. The `[package]` section sets the configuration information Cargo needs to compile your program: the name, the version, and the edition of Rust to use. The `[dependencies]` section is where you list project dependencies.

The _src/main.rs_ file should look like:

```rs
fn main() {
    println!("Hello, world!");
}
```

Cargo expects source files to live inside the _src_ directory. The top-level project directory is for non code-related files.

### Building and Running a Cargo Project

Build your project by enter the following command from the _hello\_cargo_ directory:

```sh
cargo build
```
