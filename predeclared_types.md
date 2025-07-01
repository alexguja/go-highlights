## Predeclared Types
The built-in Go types are called predeclared types. They are the basic building blocks of Go programs and include booleans, integers, floats, strings, etc. 


> [!NOTE]  
> Go assigns a default zero value to declared but unassigned variables. For example, an `int` variable will have a default value of `0`, a `bool` will be `false`, and a `string` will be an empty string `""`, etc. This eliminates a lot of bugs found in C/C++  programs.

 
### Literals

Literals the raw, direct representation of values in your code (e.g., `123`, `'a'`, `"hello"`).

Types of Literals:

- Integer Literals: Whole numbers. Can be base 10 (normal), binary (`0b`), octal (`0o` or confusingly `0`), or hexadecimal (`0x`). You can use underscores (e.g., `1_000_000`) for readability, but not at the start/end or next to each other.

- Floating-Point Literals: Numbers with decimal points (e.g., `3.14`). Can also use exponents (`6.03e23`) or hexadecimal (`0x1.999999999999ap+3`). Underscores are also allowed for readability.

- Rune Literals: Single characters, enclosed in single quotes (e.g., `'a'`). They represent Unicode characters and can be written in various hexadecimal or octal escape forms (e.g., `'\u0061'`). Common escapes include `\n` (newline), `\t` (tab), `\'`, `\"`, `\\`.

- String Literals: Sequences of characters.

- Interpreted Strings: Enclosed in double quotes (e.g., `"Hello\nWorld"`). Backslashes are used for escapes.

- Raw Strings: Enclosed in backquotes (e.g., `` `Hello\nWorld` ``). They interpret everything literally, including newlines and backslashes, except for backquotes themselves. Useful for multi-line strings or strings with many backslashes.


> [!Note]
> Practical Advice: Generally use base-10 for numbers and double quotes for strings. Avoid complex rune escapes unless they make the code much clearer. Hexadecimal/binary are sometimes used for bitwise operations or networking.

### Untyped Nature of Literals

A key concept in Go is that literals are untyped. This means a number like `100` doesn't have a specific type (like `int32` or `int64`) until it's assigned to a variable or used in an expression that forces a type.

This allows flexibility: an integer literal `100` can be used directly in a floating-point expression or assigned to a floating-point variable.

However, type compatibility still applies: you can't assign a number literal to a string variable, or a float literal to an integer variable.

There are size limitations: a literal cannot overflow the variable it's assigned to (e.g., `1000` cannot be assigned to a byte variable, which maxes out at `255`).

If a literal's type isn't clear from the context, Go assigns it a default type (e.g., `int` for integers, `float64` for floats).