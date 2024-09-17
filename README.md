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


#### 1. Basic Function Call Example

```go
// Package declaration
package main

// Import the fmt package for formatted I/O operations
import (
	"fmt"
)

// Defining a simple function f1
func f1() {
	// Currently empty function
}

// Main function where the execution starts
func main() {
	f1() // Calling f1 function
}
```

---

#### 2. Single Return Function

```go
// Define a function myFunction that takes two integers as arguments
// and returns their sum.
func myFunction(x int, y int) int {
	return x + y // Returning the sum of x and y
}

func main() {
	// Calling myFunction with 1 and 2 as arguments, and printing the result
	fmt.Println(myFunction(1, 2)) // Output: 3
}
```

---

#### 3. Function with Named Return Value

```go
// This example shows how to use a named return value.
// In this case, result is an int, and we assign it within the function.

func myFunction(x int, y int) (result int) {
	result = x + y // Assigning result the value of x + y
	return         // The return statement will return the value of result
}

func main() {
	// The function will still return the sum of 1 and 2
	fmt.Println(myFunction(1, 2)) // Output: 3
}
```

---

#### 4. Multiple Return Values

```go
// This function returns two values: an integer and a string.
// It doubles the integer and appends "World!" to the string.

func myFunction(x int, y string) (result int, txt1 string) {
	result = x + x           // result is double the value of x
	txt1 = y + " World!"     // txt1 is y appended with " World!"
	return                   // Return both result and txt1
}

func main() {
	// The function returns two values, so both need to be captured
	fmt.Println(myFunction(5, "Hello")) // Output: (10, "Hello World!")
}
```

---

#### 5. Omitting Return Values

```go
// This function still returns two values, but the caller chooses to ignore the first return value.

func myFunction(x int, y string) (result int, txt1 string) {
	result = x + x           // result is double the value of x
	txt1 = y + " World!"     // txt1 is y appended with " World!"
	return                   // Return both result and txt1
}

func main() {
	// Here, the first return value (result) is omitted by using "_".
	_, b := myFunction(5, "Hello") // Capture only the second return value (txt1)
	fmt.Println(b)                 // Output: "Hello World!"
}
```

---

#### 6. Recursive Function Example

```go
// A recursive function that prints numbers from x up to 10.
// The recursion stops when x equals 11.

func testcount(x int) int {
	if x == 11 {
		return 0  // Base case: if x is 11, stop the recursion
	}
	fmt.Println(x)      // Print the current value of x
	return testcount(x + 1) // Recursive call with x incremented by 1
}

func main() {
	// Start recursion from 1
	testcount(1) // Output: 1 2 3 4 5 6 7 8 9 10
}
```


### Variadic Functions

In Go, a variadic function is one that can accept a variable number of arguments. You define a variadic parameter by using `...` before the type. This allows you to pass zero or more arguments of the specified type.

###### Example

```go
package main

import "fmt"

// Variadic function that sums up integers
func sum(nums ...int) int {
    total := 0
    for _, num := range nums {
        total += num
    }
    return total
}

func main() {
    result := sum(1, 2, 3, 4, 5)
    fmt.Println("Sum:", result) // Output: Sum: 15
}
```

###### Explanation

- `func sum(nums ...int) int` defines a function `sum` that takes a variadic parameter `nums` of type `int`.
- Inside the function, `nums` is treated like a slice (`[]int`), so you can use range-based loops to iterate over the elements.
- When calling `sum`, you can pass any number of integers.

#### Anonymous Functions

Anonymous functions, or lambda functions, are functions defined without a name. They can be used inline where they are needed, and they are often used for short-lived operations or callbacks.

###### Example

```go
package main

import "fmt"

func main() {
    // Anonymous function assigned to a variable
    add := func(a, b int) int {
        return a + b
    }

    result := add(10, 20)
    fmt.Println("Sum:", result) // Output: Sum: 30

    // Anonymous function used immediately
    result = func(a, b int) int {
        return a * b
    }(5, 6)

    fmt.Println("Product:", result) // Output: Product: 30
}
```

###### Explanation

- `add := func(a, b int) int { ... }` creates an anonymous function and assigns it to the variable `add`.
- This function can then be invoked like a regular function.
- You can also define and call an anonymous function immediately, as shown in the second part of the example.




### Understanding the `init` Function in Go

#### Overview

In Go, the `init` function is a special function that is executed automatically when a package is imported. It is used for initialization tasks that need to be completed before the `main` function starts executing. The `init` function does not take any arguments and does not return any values. 

#### Key Characteristics

- **Execution Order**: The `init` function is executed before the `main` function.
- **Multiple `init` Functions**: You can have multiple `init` functions in a single file, and they are executed in the order they appear.
- **Multiple Packages**: When dealing with multiple packages, the `init` functions are executed in a specific order based on the package import hierarchy.

#### Example 1: Basic Usage

In this example, we demonstrate how the `init` function initializes variables before the `main` function is executed.

```go
package main

import "fmt"

// Package-level variables
var greetings string
var age int

// Init function
func init() {
    fmt.Println("I always execute before main() function")
    greetings = "Hello world"
}

// Main function
func main() {
    fmt.Println("I execute after init() function")
    fmt.Println(greetings)
    fmt.Printf("Go language is %d years old \n", age)
}
```

##### Output

```
I always execute before main() function
I execute after init() function
Hello world
Go language is 0 years old
```

##### Explanation

- The `init` function sets the `greetings` variable before `main` executes.
- The `main` function prints the values initialized by `init`, demonstrating that `init` executes first.

#### Example 2: Multiple `init` Functions in a File

You can define multiple `init` functions within the same file. They are executed in the order they are defined.

```go
package main

import "fmt"

// First init function
func init() {
    fmt.Println("<<< First >>>")
}

// Second init function
func init() {
    fmt.Println("<<< Second >>>")
}

// Third init function
func init() {
    fmt.Println("<<< Third >>>")
}

// Main function
func main() {
    fmt.Println("I execute after init() functions")
}
```

##### Output

```
<<< First >>>
<<< Second >>>
<<< Third >>>
I execute after init() functions
```

##### Explanation

- The `init` functions are executed in the order they appear in the file.
- The `main` function runs after all `init` functions have completed.

#### Example 3: Multiple Packages with `init` Functions

When working with multiple packages, `init` functions in different packages are executed in a specific order based on import dependencies.

```go
// File: a/a.go
package a

func init() {
    println("init() function in a/a.go")
}

func Greetings() {
    println("Hello, world from a/a.go")
}

// File: b/b.go
package b

import "fmt"

func init() {
    fmt.Println("init() function in b/b.go")
}

func Greetings() {
    fmt.Println("Hello, world from b/b.go")
}

// File: main.go
package main

import (
    "fmt"
    "a" // import package a
    "b" // import package b
)

func init() {
    fmt.Println("init() function in main.go")
}

func main() {
    fmt.Println("Executing main() function in main.go")
    a.Greetings()
    b.Greetings()
}
```

##### Output

```
init() function in a/a.go
init() function in b/b.go
init() function in main.go
Executing main() function in main.go
Hello, world from a/a.go
Hello, world from b/b.go
```

##### Explanation

1. **Package `a`**:
   - The `init` function in package `a` executes first, as it is the first package imported.

2. **Package `b`**:
   - The `init` function in package `b` executes next, following the import of package `b`.

3. **Main Package**:
   - The `init` function in the `main` package executes after the `init` functions in imported packages.

4. **Execution Order**:
   - The `main` function starts executing last, after all `init` functions have been completed.

#### Conclusion

The `init` function in Go plays a crucial role in package initialization, allowing setup tasks to be performed before the `main` function runs. It can be used in multiple ways, including defining multiple `init` functions within a file and handling initialization across multiple packages. Understanding the order of execution for `init` functions is essential for managing complex initialization logic in Go applications.
```

```
### Understanding Structs in Go

#### Overview

In Go, a `struct` (short for structure) is a composite data type that groups together variables (fields) under a single name. Structs are used to create complex data types that group different pieces of related data together. They are a foundational concept in Go, enabling the modeling of real-world entities and structures.

#### Defining a Struct

A struct is defined using the `type` keyword followed by the struct name and the `struct` keyword. Fields within a struct are defined with their name and type.

##### Syntax

```go
type StructName struct {
    FieldName1 FieldType1
    FieldName2 FieldType2
    // Additional fields
}
```

##### Example

```go
type Person struct {
    Name    string
    Age     int
    Address string
}
```

#### Creating and Initializing Structs

Structs can be instantiated and initialized in various ways, including using literal notation or the `new` keyword.

##### Using Struct Literals

You can initialize a struct by providing values for its fields in a struct literal.

```go
// Creating an instance of Person using struct literal
person := Person{
    Name:    "Alice",
    Age:     30,
    Address: "123 Wonderland",
}
```

##### Using the `new` Keyword

The `new` keyword creates a pointer to a new struct and initializes all fields to their zero values.

```go
// Creating a pointer to a new Person instance
personPtr := new(Person)
personPtr.Name = "Bob"
personPtr.Age = 25
personPtr.Address = "456 Neverland"
```

#### Accessing Struct Fields

Struct fields are accessed using dot notation.

##### Example

```go
fmt.Println(person.Name)    // Output: Alice
fmt.Println(person.Age)     // Output: 30
fmt.Println(person.Address) // Output: 123 Wonderland
```

#### Struct Methods

You can define methods on structs to perform operations on the struct data. Methods are functions with a receiver argument that specifies the struct type.

##### Syntax

```go
func (s StructName) MethodName(params) returnType {
    // Method body
}
```

##### Example

```go
type Person struct {
    Name    string
    Age     int
    Address string
}

// Method to display person details
func (p Person) DisplayInfo() {
    fmt.Printf("Name: %s, Age: %d, Address: %s\n", p.Name, p.Age, p.Address)
}
```

##### Usage

```go
person := Person{Name: "Charlie", Age: 35, Address: "789 Imaginary"}
person.DisplayInfo() // Output: Name: Charlie, Age: 35, Address: 789 Imaginary
```

#### Struct Pointers

Structs can be used with pointers to avoid copying the entire struct when passing it to functions or methods. This is especially useful for large structs or when you need to modify the original struct.

##### Example

```go
type Person struct {
    Name string
    Age  int
}

// Method with a pointer receiver to modify the struct
func (p *Person) CelebrateBirthday() {
    p.Age++
}

func main() {
    person := Person{Name: "David", Age: 40}
    person.CelebrateBirthday()
    fmt.Println(person.Age) // Output: 41
}
```

#### Embedded Structs

Go supports struct embedding, allowing one struct to include another struct as a field. This provides a way to achieve composition and reuse.

##### Example

```go
type Address struct {
    Street string
    City   string
}

type Person struct {
    Name    string
    Age     int
    Address // Embedded struct
}

func main() {
    person := Person{
        Name:    "Eve",
        Age:     28,
        Address: Address{Street: "101 Main St", City: "Metropolis"},
    }
    fmt.Println(person.Name)       // Output: Eve
    fmt.Println(person.Street)     // Output: 101 Main St
    fmt.Println(person.City)       // Output: Metropolis
}
```

#### Struct Tags

Struct tags are metadata associated with struct fields. They are often used for encoding/decoding with libraries such as JSON or XML.

##### Example

```go
type Person struct {
    Name    string `json:"name"`
    Age     int    `json:"age"`
    Address string `json:"address"`
}
```

##### Usage with JSON

```go
import (
    "encoding/json"
    "fmt"
)

func main() {
    person := Person{Name: "Frank", Age: 50, Address: "102 Elm St"}
    data, _ := json.Marshal(person)
    fmt.Println(string(data)) // Output: {"name":"Frank","age":50,"address":"102 Elm St"}
}
```

#### Anonymous Structs

Anonymous structs are structs without a named type. They are used for quick and temporary data grouping, often in situations where defining a named struct type is unnecessary.

##### Creating Anonymous Structs

Anonymous structs are created inline, usually when you need a struct for a specific purpose and don’t need to reuse it elsewhere.

##### Example

```go
func main() {
    // Creating an anonymous struct
    person := struct {
        Name    string
        Age     int
        Address string
    }{
        Name:    "Grace",
        Age:     29,
        Address: "789 Unknown",
    }

    fmt.Println(person.Name)    // Output: Grace
    fmt.Println(person.Age)     // Output: 29
    fmt.Println(person.Address) // Output: 789 Unknown
}
```

##### Usage

Anonymous structs are useful for scenarios such as:

- Temporary data storage in functions.
- Returning multiple values from a function in a single structured form.
- Passing complex data between functions or methods without creating a formal type.

#### Conclusion

Structs in Go are a powerful feature that allows you to define and work with complex data structures. They support various operations such as initialization, field access, method definition, embedding, and the use of struct tags. Anonymous structs provide a way to quickly group data without creating a named type. Understanding structs and their capabilities is essential for effective Go programming.
```
