# Chapter 3: Basics

## 3.1 Variables

* declare a variable using the `let` keyword
  ```rust
  let power_level = 9000;
  ```
  if you try to change the immutable variable after declaration,
  the compiler will scold you
  - btw all statements end in a semicolon
* all variables are immutable by default
* you can make a variable mutable by explicitly using the `mut` keyword
  ```rust
  let mut power_level = 9000;
  power_level = 9000 + 1;
  ```
* constants can only be computed at compile time
  - this means they have to be made up of primitive literals (not a
    returned value of a function call)
  ```rust
  const IPv4_TOTAL_IPS: u64 = 256 * 256 * 256 * 256;
  const IPv6_TOTAL_IPS: u128 = 65536 * 65536 * 65536 * 65536 * 65536 * 65536 * 65536 * 65536;
  // IPv6 will actually fail because 128 bits is not enough to represent the total (T-T)
  // let's make u256 happen!
  ```
* you can get a kind of temporary mutability with shadowing.
  there's two ways to do this:
  - 1) redeclaration
    ```rust
    let spaces = "    ";
    let spaces = spaces.len();
    ```
    - this is useful for initialization of a variable that can be
      immutable for the rest of the lifetime of the program.
      this is kind of similar to the Builder Pattern seen in Java,
      but in different statements rather than chained functions.
      it is also useful as you can redeclare a variable with different
      types. it lets us avoid declaring variables of different types,
      with the type appended to the name, like `spaces_str` and `spaces_num`.
  - 2) scope
    ```rust
    let x = 2;
    {
        let x = x * 2;
        println!("{x}")
    }
    println!("{x}")
    ```
    - this is useful for a value that can change within a particular scope,
      and it can even reference the original value,
      but when we return to the original scope it returns to the original value

## 3.2 Data Types

Two categories of data types: scalar and compound
* Scalar - a single thing
* Compound - many things, a group of things

### Scalars
* Numbers
  * integer and floating-point
  * integers can be signed (positive & negative) or unsigned (positive only)
  * number bit size can be specified directly
    - `i8`, `i16`, `i32`, `i64`, `i128`
    - `u8`, `u16`, `u32`, `u64`, `u128`
    - `f32`, `f64`
    - `isize`, `usize` << these are specific to your architecture and
      basically let you infer the register size of your CPU
  * default integer type is `i32`, default float type is `f64`
  * you can write number literals in various radix formats
    - decimal (base-10) is the default: `1048576`
    - hex (base-16): `0x100000`
    - octal (base-8): `0o4000000`
    - binary (base-2): `0b10000000000000000000000000000000000000000`
  * you can add an underscore to number literals to make it more readable
    `1_048_576`
  * basic operations are supported: `+ - * / %`
* Character
  * single characters are represented with single quotes
  ```rust
  fn main() {
      let c = 'z';
      let z: char = 'ℤ'; // with explicit type annotation
      let heart_eyed_cat = '😻';
  }
  ```

### Compound Types
* Tuples
  * a fixed-size group of values (can be different types)
  * we can use pattern matching (Ch. 6) to destructure the tuple
  * you can also reference tuple members directly with explicit indexing
    ```rust
    fn main() {
        let tup: (i32, f64, u8) = (500, 6.4, 1);

        // destructuring
        let (x, y, z) = tup;
        println!("x:{x}, y:{y}, z:{z}");

        // explicit index
        println!("x:{}, y:{}, z:{}", tup.0, tup.1, tup.2);
    }
    ```
  * an empty tuple is called a Unit, its initialized as `()`
  and its type is also `()`. expressions implicitly return a unit if
  they don't return any other value.
* Arrays
  * ordered groups of the same type
  * fixed length at declaration time
  * indexed array access
    ```rust
    fn main() {
        let a = [1, 2, 3, 4, 5];
        let first = a[0];
        let second = a[1];
    }
    ```
  * you can declare size and initialize all the values to a particular value
    ```rust
        let a = [1; 5]; // initializes [1, 1, 1, 1, 1]
    ```
  * if you try to access an array out of bounds at runtime, it will panic
    - a panic is a critical runtime error, your rust program will exit
    - if you try to access an array out of bounds at compile time,
      it will not compile (what a good compiler)


## 3.3 Functions

## 3.4 Comments

## Control Flow
