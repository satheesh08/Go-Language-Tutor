# `Go Language`

### `Go Syntax`
- Package Declaration
- Import Package
- Function
- Statements and Expressions

### `Basic Code`
```go
package main  //this program belongs to main package

import("fmt") // import fomrat predefined library and its function

func main(){
    fmt.println("Hello World !"); // function from the package
}
```

#### `Execution`
- Save the file as .go
- VS Code > Terminal > go run .\hello.go
- VS Code > Terminal> go build .\hello.go 

#### `Commenting`
```go
//    Single Line Comment
/*  Multi Line Comment */
```

#### `Info`
- No Error
```go
func main(){
    fmt.println("Hello World !");
}
```


- Throws Error  **{**  should not start
```go
func main()
{
    fmt.println("Hello World !");
}
```

### `Go Data Types`
| Data Type | Explanation |
| --------- | ----------- |
| int8	| 8-bit signed integer|
| int16	| 16-bit signed integer|
| int32	| 32-bit signed integer|
| int64	| 64-bit signed integer|
| uint8	| 8-bit unsigned integer|
| uint16 |	16-bit unsigned integer|
| uint32 |	32-bit unsigned integer|
| uint64 |	64-bit unsigned integer|
| int	| Both int and uint contain same size, either 32 or 64 bit.|
| uint	 | Both int and uint contain same size, either 32 or 64 bit.|
| rune	| It is a synonym of int32 and also represent Unicode code points.|
| byte	| It is a synonym of uint8.|
| uintptr	| It is an unsigned integer type. Its width is not defined, but its can hold all the bits of a pointer value. |

### 1. **`int8`, `int16`, `int32`, `int64`**
```go
package main

import "fmt"

func main() {
    var a int8 = -128      // 8-bit signed integer
    var b int16 = -32768   // 16-bit signed integer
    var c int32 = -2147483648 // 32-bit signed integer
    var d int64 = -9223372036854775808 // 64-bit signed integer
    
    fmt.Println(a, b, c, d) // Output: -128 -32768 -2147483648 -9223372036854775808
}
```

### 2. **`uint8`, `uint16`, `uint32`, `uint64`**
```go
package main

import "fmt"

func main() {
    var e uint8 = 255        // 8-bit unsigned integer
    var f uint16 = 65535     // 16-bit unsigned integer
    var g uint32 = 4294967295 // 32-bit unsigned integer
    var h uint64 = 18446744073709551615 // 64-bit unsigned integer
    
    fmt.Println(e, f, g, h) // Output: 255 65535 4294967295 18446744073709551615
}
```

### 3. **`int`, `uint`**
```go
package main

import "fmt"

func main() {
    var i int = -42      // 32-bit or 64-bit signed integer (depends on architecture)
    var j uint = 42      // 32-bit or 64-bit unsigned integer (depends on architecture)
    
    fmt.Println(i, j)    // Output depends on architecture: -42 42
}
```

### 4. **`rune`**
```go
package main

import "fmt"

func main() {
    var r rune = 'A'  // Unicode code point (int32)
    
    fmt.Printf("Rune: %c, Unicode: %U\n", r, r) // Output: Rune: A, Unicode: U+0041
}
```

### 5. **`byte`**
```go
package main

import "fmt"

func main() {
    var b byte = 'A'  // Same as uint8
    fmt.Printf("Byte: %c, Value: %d\n", b, b) // Output: Byte: A, Value: 65
}
```

### 6. **`uintptr`**
```go
package main

import "fmt"

func main() {
    var x int = 100
    var ptr uintptr = uintptr(&x) // Converts pointer to uintptr
    
    fmt.Printf("Pointer: %x\n", ptr) // Output: Hexadecimal memory address
}
```
### **`Go Variables`**

#### **Rules for Variable Names:**
- Must start with a letter or underscore (`_`).
- Cannot start with a digit.
- Can contain alphanumeric characters (`A-Z`, `a-z`, `0-9`) or an underscore (`_`).
- Go is case-sensitive (e.g., `age` and `Age` are different variables).
- There is no limit on the length of a variable name.
- Variable names cannot contain spaces.
- Keywords cannot be used as variable names.

#### **Syntax for Variable Declaration:**
```go
var variableName type = value;
```

#### **Examples:**

1. **Explicit Type Declaration**
    ```go
    var a string = "Isaac"  // Declaring the type explicitly as string
    ```

2. **Type Inference**
    ```go
    var a string = "Isaac"
    var b : a  // Type is inferred by the compiler (string in this case)
    var b = "Isaac"  // Type is inferred by the compiler (string in this case)
    ```

3. **Declaration Without Initialization**
    ```go
    var a string    // Declaring the variable, no value assigned yet
    a = "J"         // Assigning value later
    ```
4. **In Block**
    ```go
    var(
        a int
        b int=1
        c string="Hello"
    )
    ```

5. **Multiple Declaration**
    ```go
    var a,b = 6,"hello"
    var a,b int = 1,3
    ```

In Go, the `:=` syntax is used for **short variable declaration**, allowing you to both declare and initialize a variable in a concise way. It is primarily used when you want the Go compiler to infer the variable's type based on the value assigned. Here are the key scenarios and rules for using `:=`:

### When to Use `:=`:

1. **Inside Functions**: `:=` can only be used within function bodies (local scope). It cannot be used for declaring variables at the package level (outside functions).
   ```go
   func main() {
       name := "Isaac"  // Compiler infers the type as string
   }
   ```

2. **Type Inference**: When you want the compiler to infer the type of the variable based on the assigned value.
   ```go
   func main() {
       x := 42          // Compiler infers the type as int
       pi := 3.14       // Compiler infers the type as float64
       isActive := true // Compiler infers the type as bool
   }
   ```

3. **Multiple Variable Declaration**: You can use `:=` to declare and initialize multiple variables at once.
   ```go
   func main() {
       a, b := 10, "hello"  // a is int, b is string
   }
   ```

4. **Reassigning at Least One Variable**: If one or more variables in a multi-variable assignment are already declared, you can still use `:=` to redeclare and assign new values to the others.
   ```go
   func main() {
       x := 5
       x, y := 10, 20 // x is reassigned to 10, y is newly declared as 20
   }
   ```

### When Not to Use `:=`:

1. **Outside Functions**: `:=` cannot be used at the package level (outside a function). Use `var` for global variables.
   ```go
   var globalVar = "Outside function"  // Correct way to declare at package level
   ```

2. **When You Need a Specific Type**: If you want to explicitly declare the type of a variable, use the `var` keyword instead of `:=`.
   ```go
   var num int = 42  // Declaring a variable with a specific type
   ```

### Example of `:=` in Use:

```go
package main

import "fmt"

func main() {
    name := "Alice"   // Compiler infers the type as string
    age := 30         // Compiler infers the type as int
    isStudent := false // Compiler infers the type as bool

    fmt.Println(name, age, isStudent)  // Output: Alice 30 false
}
```

In summary, use `:=` for local variable declarations inside functions when you want concise code and type inference. Use the `var` keyword when you need to declare a variable globally or specify its type explicitly.    
---

### **Go Constants**

Constants in Go are **fixed values** that **cannot be changed** once declared.

---

#### **Syntax for Constants:**
- Constants are declared using the `const` keyword, similar to variables.
- By convention, constant names are often written in **uppercase**.
- Constants can be declared both **inside and outside** of functions.

---

### **Types of Constants:**

#### **1. Typed Constants**
- The type of the constant is explicitly declared.
    ```go
    const A int = 1
    ```

#### **2. Untyped Constants**
- The type of the constant is inferred by the compiler.
    ```go
    const A = 1
    ```

---

### **Multiple Constants Declaration:**
- You can declare multiple constants in a block.
    ```go
    const (
        A int = 1
        B int = 2
    )
    ```

---

### **Example:**

```go
package main

import "fmt"

// Global constants
const (
    PI  float64 = 3.14
    E   = 2.71 // Untyped
)

func main() {
    const GREETING = "Hello, Go!"  // Constant inside a function

    fmt.Println(PI)       // Output: 3.14
    fmt.Println(E)        // Output: 2.71
    fmt.Println(GREETING) // Output: Hello, Go!
}
```

### **Printing and Formatting Verbs in Go**

Go provides several functions for printing and formatting, primarily from the `fmt` package. Commonly used functions include:

- `fmt.Print()`: Prints the text without formatting.
- `fmt.Println()`: Prints the text followed by a newline.
- `fmt.Printf()`: Prints formatted text.

---

### **Formatting Verbs in Go:**

Go uses **formatting verbs** for printing variables in specific formats using `fmt.Printf()`.

Here’s a more **complete list** of the Go formatting verbs, with their explanations and examples:

### **Complete List of Go Formatting Verbs**

#### **General Verbs:**
| Verb  | Description                               | Example Output        |
|-------|-------------------------------------------|-----------------------|
| `%v`  | Default format for the value               | `fmt.Printf("%v", 42)` -> `42` |
| `%+v` | Prints struct with field names             | `fmt.Printf("%+v", myStruct)` -> `{Field1: 10 Field2: 20}` |
| `%#v` | Go-syntax representation                  | `fmt.Printf("%#v", myStruct)` -> `main.MyStruct{Field1: 10, Field2: 20}` |
| `%T`  | Type of the value                         | `fmt.Printf("%T", 42)` -> `int` |
| `%%`  | Literal percent sign                      | `fmt.Printf("%%")` -> `%` |

---

#### **Integer Verbs:**
| Verb  | Description                               | Example Output        |
|-------|-------------------------------------------|-----------------------|
| `%d`  | Decimal integer                           | `fmt.Printf("%d", 42)` -> `42` |
| `%b`  | Binary format                             | `fmt.Printf("%b", 42)` -> `101010` |
| `%o`  | Octal format                              | `fmt.Printf("%o", 42)` -> `52` |
| `%x`  | Hexadecimal (lowercase)                   | `fmt.Printf("%x", 42)` -> `2a` |
| `%X`  | Hexadecimal (uppercase)                   | `fmt.Printf("%X", 42)` -> `2A` |
| `%c`  | Character (Unicode)                       | `fmt.Printf("%c", 65)` -> `A` |
| `%U`  | Unicode format (character + code point)   | `fmt.Printf("%U", 65)` -> `U+0041` |
| `%q`  | Single-quoted character                   | `fmt.Printf("%q", 65)` -> `'A'` |

---

#### **Floating-Point and Complex Verbs:**
| Verb  | Description                               | Example Output        |
|-------|-------------------------------------------|-----------------------|
| `%f`  | Decimal point but no exponent             | `fmt.Printf("%f", 3.14)` -> `3.140000` |
| `%.2f`| Decimal point, with precision             | `fmt.Printf("%.2f", 3.14)` -> `3.14` |
| `%e`  | Scientific notation (lowercase)            | `fmt.Printf("%e", 3.14)` -> `3.140000e+00` |
| `%E`  | Scientific notation (uppercase)            | `fmt.Printf("%E", 3.14)` -> `3.140000E+00` |
| `%g`  | Compact representation                    | `fmt.Printf("%g", 3.14)` -> `3.14` |
| `%G`  | Compact representation (uppercase)        | `fmt.Printf("%G", 3.14)` -> `3.14` |
| `%x`  | Hexadecimal notation (with fraction)       | `fmt.Printf("%x", 3.14)` -> `0x1.91eb851eb851fp+1` |
| `%p`  | Pointer                                   | `fmt.Printf("%p", &a)` -> `0x123456` |

---

#### **String and Slice Verbs:**
| Verb  | Description                               | Example Output        |
|-------|-------------------------------------------|-----------------------|
| `%s`  | String                                    | `fmt.Printf("%s", "hello")` -> `hello` |
| `%q`  | Double-quoted string with escaped characters | `fmt.Printf("%q", "hello")` -> `"hello"` |
| `%x`  | Hex dump of string (lowercase)            | `fmt.Printf("%x", "abc")` -> `616263` |
| `%X`  | Hex dump of string (uppercase)            | `fmt.Printf("%X", "abc")` -> `616263` |
| `%p`  | Pointer                                   | `fmt.Printf("%p", &str)` -> `0x123456` |

---

#### **Boolean Verbs:**
| Verb  | Description                               | Example Output        |
|-------|-------------------------------------------|-----------------------|
| `%t`  | Boolean (true/false)                      | `fmt.Printf("%t", true)` -> `true` |

---

#### **Pointer Verbs:**
| Verb  | Description                               | Example Output        |
|-------|-------------------------------------------|-----------------------|
| `%p`  | Pointer address                           | `fmt.Printf("%p", &a)` -> `0x123456` |

---

#### **Width and Precision Control:**
| Verb     | Description                                | Example Output        |
|----------|--------------------------------------------|-----------------------|
| `%5d`    | Pad integer with spaces (right-aligned)     | `fmt.Printf("%5d", 42)` -> `   42` |
| `%-5d`   | Pad integer with spaces (left-aligned)      | `fmt.Printf("%-5d", 42)` -> `42   ` |
| `%05d`   | Pad integer with zeros (right-aligned)      | `fmt.Printf("%05d", 42)` -> `00042` |
| `%7.2f`  | Width and precision for floating-point      | `fmt.Printf("%7.2f", 3.14)` -> `   3.14` |

---

#### **Example Usage:**

```go
package main

import "fmt"

func main() {
    // General Formatting
    name := "Go"
    age := 10
    pi := 3.14159

    fmt.Printf("Name: %s, Age: %d, Pi: %.2f\n", name, age, pi)  // Name: Go, Age: 10, Pi: 3.14
    fmt.Printf("Binary Age: %b, Hex Age: %x\n", age, age)       // Binary Age: 1010, Hex Age: a
    fmt.Printf("Type of pi: %T\n", pi)                         // Type of pi: float64

    // String and Unicode formatting
    fmt.Printf("Quoted: %q\n", "Hello, Go!")                   // Quoted: "Hello, Go!"
    fmt.Printf("Character: %c\n", 65)                          // Character: A

    // Width and Precision
    fmt.Printf("Padded integer: %5d\n", 42)                    // Padded integer:    42
    fmt.Printf("Padded float: %7.2f\n", pi)                    // Padded float:    3.14
}
```

Here is a comprehensive list of all **Go language operators** in markdown format:

### **Go Operators**

#### **1. Arithmetic Operators:**
| Operator | Description              | Example                |
|----------|--------------------------|------------------------|
| `+`      | Addition                 | `x + y` (sum of `x` and `y`)  |
| `-`      | Subtraction              | `x - y` (difference between `x` and `y`) |
| `*`      | Multiplication           | `x * y` (product of `x` and `y`)  |
| `/`      | Division                 | `x / y` (quotient of `x` divided by `y`) |
| `%`      | Modulus (remainder)      | `x % y` (remainder of `x` divided by `y`) |

---

#### **2. Relational (Comparison) Operators:**
| Operator | Description              | Example                |
|----------|--------------------------|------------------------|
| `==`     | Equal to                 | `x == y` (checks if `x` is equal to `y`) |
| `!=`     | Not equal to             | `x != y` (checks if `x` is not equal to `y`) |
| `>`      | Greater than             | `x > y` (checks if `x` is greater than `y`) |
| `<`      | Less than                | `x < y` (checks if `x` is less than `y`) |
| `>=`     | Greater than or equal to | `x >= y` (checks if `x` is greater than or equal to `y`) |
| `<=`     | Less than or equal to    | `x <= y` (checks if `x` is less than or equal to `y`) |

---

#### **3. Logical (Boolean) Operators:**
| Operator | Description              | Example                |
|----------|--------------------------|------------------------|
| `&&`     | Logical AND              | `x && y` (true if both `x` and `y` are true) |
| \|\|    | Logical OR               | `x \|\| y` (true if either `x` or `y` is true) |
| `!`      | Logical NOT              | `!x` (true if `x` is false) |

---

#### **4. Bitwise Operators:**
| Operator | Description              | Example                |
|----------|--------------------------|------------------------|
| `&`      | Bitwise AND              | `x & y` (bitwise AND of `x` and `y`) |
| \|      | Bitwise OR               | `x \| y` (bitwise OR of `x` and `y`) |
| `^`      | Bitwise XOR              | `x ^ y` (bitwise XOR of `x` and `y`) |
| `&^`     | Bit Clear (AND NOT)      | `x &^ y` (bitwise AND NOT of `x` and `y`) |
| `<<`     | Left shift               | `x << n` (shift `x` left by `n` bits) |
| `>>`     | Right shift              | `x >> n` (shift `x` right by `n` bits) |

---

#### **5. Assignment Operators:**
| Operator | Description              | Example                |
|----------|--------------------------|------------------------|
| `=`      | Assign                   | `x = y` (assigns `y` to `x`) |
| `+=`     | Add and assign            | `x += y` (adds `y` to `x` and assigns to `x`) |
| `-=`     | Subtract and assign       | `x -= y` (subtracts `y` from `x` and assigns to `x`) |
| `*=`     | Multiply and assign       | `x *= y` (multiplies `x` by `y` and assigns to `x`) |
| `/=`     | Divide and assign         | `x /= y` (divides `x` by `y` and assigns to `x`) |
| `%=`     | Modulus and assign        | `x %= y` (assigns remainder of `x` divided by `y` to `x`) |
| `<<=`    | Left shift and assign     | `x <<= n` (left shifts `x` by `n` bits and assigns to `x`) |
| `>>=`    | Right shift and assign    | `x >>= n` (right shifts `x` by `n` bits and assigns to `x`) |
| `&=`     | Bitwise AND and assign    | `x &= y` (bitwise AND `x` with `y` and assigns to `x`) |
| `\|=`     | Bitwise OR and assign     | `x \|= y` (bitwise OR `x` with `y` and assigns to `x`) |
| `^=`     | Bitwise XOR and assign    | `x ^= y` (bitwise XOR `x` with `y` and assigns to `x`) |
| `&^=`    | Bit clear (AND NOT) and assign | `x &^= y` (bitwise AND NOT `x` with `y` and assigns to `x`) |

---

#### **6. Miscellaneous Operators:**
| Operator | Description              | Example                |
|----------|--------------------------|------------------------|
| `&`      | Address of               | `&x` (returns the memory address of `x`) |
| `*`      | Pointer dereference      | `*p` (dereferences pointer `p`) |
| `...`    | Variadic arguments       | `func(args ...int)` (function accepts a variable number of arguments) |

---

#### **7. Increment/Decrement Operators:**
| Operator | Description              | Example                |
|----------|--------------------------|------------------------|
| `++`     | Increment                | `x++` (increments `x` by 1) |
| `--`     | Decrement                | `x--` (decrements `x` by 1) |

---

#### **Operator Precedence (Highest to Lowest):**
1. `*`  `/`  `%`  `<<`  `>>`  `&`  `&^`
2. `+`  `-`  `|`  `^`
3. `==`  `!=`  `<`  `<=`  `>`  `>=`
4. `&&`
5. `||`

---

This list covers **all major operators** in Go, including arithmetic, relational, logical, bitwise, assignment, and miscellaneous operators, as well as their examples and explanations.

Here’s an expanded version including **`range`** and **multi-value `switch`** statements in **Go**:

### **Go Control Statements**

#### **1. If-Else Statements**
The `if` statement is used to execute code based on conditions, with optional `else` and `else if` blocks.

```go
if condition {
    // Code when condition is true
} else {
    // Code when condition is false
}
```

#### **2. Switch Statement**
A cleaner alternative to multiple `if-else` conditions, `switch` checks multiple cases.

```go
switch variable {
case value1:
    // Code when variable == value1
case value2:
    // Code when variable == value2
default:
    // Code if no cases match
}
```

#### **Multi-value Switch:**
In Go, you can match multiple values in a single `case`.

```go
switch day {
case "Saturday", "Sunday":
    fmt.Println("It's the weekend!")
default:
    fmt.Println("It's a weekday.")
}
```

#### **Switch with Expressions:**
Switch cases can evaluate expressions.

```go
switch {
case x < 0:
    fmt.Println("Negative")
case x == 0:
    fmt.Println("Zero")
default:
    fmt.Println("Positive")
}
```

---

#### **3. For Loop**
The only looping construct in Go.

##### **3.1 Basic `for` Loop:**
```go
for initializer; condition; post {
    // Code to execute in each iteration
}
```

##### **3.2 `for` as While Loop:**
```go
for condition {
    // Loop runs while condition is true
}
```

##### **3.3 Infinite Loop:**
```go
for {
    // Infinite loop
}
```

---

#### **4. Range in Loops**
The `range` keyword is used in loops to iterate over elements of arrays, slices, maps, and channels.

##### **4.1 Iterating Over a Slice:**
```go
numbers := []int{1, 2, 3, 4, 5}
for i, num := range numbers {
    fmt.Printf("Index: %d, Value: %d\n", i, num)
}
```

- `i` is the index and `num` is the value at that index.
- If you don't need the index, use `_`:
  
```go
for _, num := range numbers {
    fmt.Println(num)
}
```

##### **4.2 Iterating Over a Map:**
```go
person := map[string]string{"name": "Alice", "city": "Wonderland"}
for key, value := range person {
    fmt.Printf("%s: %s\n", key, value)
}
```

##### **4.3 Iterating Over a String:**
When iterating over a string, `range` returns the index and the rune (Unicode code point).

```go
for i, r := range "GoLang" {
    fmt.Printf("Index: %d, Rune: %c\n", i, r)
}
```

---

#### **5. Break Statement**
Exits from the current loop or switch.

```go
for i := 0; i < 5; i++ {
    if i == 3 {
        break // Exits the loop when i == 3
    }
    fmt.Println(i)
}
```

---

#### **6. Continue Statement**
Skips the remaining code in the current iteration of the loop and moves to the next iteration.

```go
for i := 0; i < 5; i++ {
    if i%2 == 0 {
        continue // Skip even numbers
    }
    fmt.Println(i)
}
```

---

#### **7. Goto Statement**
Jumps to a labeled statement. Use sparingly, as it can lead to complex, unreadable code.

```go
func main() {
    x := 10
    if x > 5 {
        goto Label
    }
    fmt.Println("This won't execute")

Label:
    fmt.Println("Jumped to label!")
}
```

---

#### **8. Defer Statement**
Schedules a function call to run after the surrounding function completes.

```go
func main() {
    defer fmt.Println("This will run last.")
    fmt.Println("This will run first.")
}
```

- **Deferred function calls** are executed in **LIFO (Last In, First Out)** order.

---

#### **9. Panic and Recover**
- **`panic`**: Stops normal execution and begins panicking.
- **`recover`**: Regains control of a panicking goroutine.

```go
func main() {
    defer func() {
        if r := recover(); r != nil {
            fmt.Println("Recovered from panic:", r)
        }
    }()
    panic("Something went wrong!")
}
```

---

### **Additional Switch Concepts**

#### **Switch with Fallthrough:**
In Go, switch cases **do not fall through by default**. You must use the `fallthrough` keyword to explicitly continue to the next case.

```go
switch num {
case 1:
    fmt.Println("One")
    fallthrough
case 2:
    fmt.Println("Two")
default:
    fmt.Println("Default")
}
```

#### **Switch with Initialization Statement:**
Switch can include a short statement before evaluating the cases.

```go
switch x := 10; {
case x > 0:
    fmt.Println("x is positive")
case x < 0:
    fmt.Println("x is negative")
default:
    fmt.Println("x is zero")
}
```

---
