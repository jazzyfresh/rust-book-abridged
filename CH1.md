# Chapter 1: Installation

## 1.1 Install Rustup and the C Compiler

Rustup is a tool for managing different versions of Rust
- [ ] Download Rust
  - Windows: Find the [installer](https://forge.rust-lang.org/infra/other-installation-methods.html#standalone-installers) for your architecture 
  and you can follow the [installation guide](https://rust-lang.github.io/rustup/installation/windows-msvc.html)
  - Unix (MacOS/Linux/etc): Run this script
  ```bash
  curl --proto '=https' --tlsv1.2 https://sh.rustup.rs -sSf | sh
  ```
- [ ] Download a C Compiler (Rust needs the Linker that comes with it)
  - Windows: Install VScode or VistualStudio
  - MacOS: `xcode-select --install`
  - Linux: `sudo apt install build-essential`

- [ ] Confirm your installation
  ```bash
  rustc --version
  ```

## 1.2 Hello, World
Write the simplest Rust program
- [ ] Create a file `hello.rs`
- [ ] Add the following code
  ```rust
  fn main() {
      println!("Hello, world!");
  }
  ```
  This code contains the `main()` function, which is the entrypoint
  to every Rust program. It prints a message to stdout using `println!()`.
- [ ] Compile your code with the rust compiler
  ```bash
  rustc hello.rs
  ```
- [ ] Run the binary executable that was created for your Rust program
  - Windows
  ```bash
  .\hello.exe
  ```
  - Unix
  ```bash
  ./hello
  ```

## 1.3 Hello, Cargo
Cargo is the package manager and build tool for Rust.
It helps you create larger projects, build multiple interdependent
Rust files, manage dependencies, as well as release your software.
It's all around great!

- [ ] Verify your Cargo installation (it should have been installed by Rustup)
  ```bash
  cargo --version
  ```
- [ ] Use Cargo to build a project template
  ```bash
  cargo new hello_cargo
  ```
  This creates a directory that contains your Rust project
- [ ] Build and run your Rust project
  ```bash
  cd hello_cargo
  cargo run
  ```
  You can also build the project binary and run it, similar to before:
  - Windows
    ```bash
    cargo build
    .\target\debug\hello_cargo.exe
    ```
  - Unix
    ```bash
    cargo build
    ./target/debug/hello_cargo
    ```
  You can also compile the code to check for errors, but not run it:
  ```bash
  cargo check
  ```
  NOTE: Cargo automatically initializes a new Git repo for your project,
  which is cool, but sometimes you already have a Git repo or you want it
  to contain more than just your Rust project. In those cases, just run
  `cargo new` inside of an exising Git repo.

You are ready to write Rust!
