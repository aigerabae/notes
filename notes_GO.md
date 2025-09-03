### Packages:
example that they provide in the video:
```go
package main

import "github.com/01-edu/z01"

func main() {
  zo1.PrintRune('a')
  z01.PrintRune('\n)
}
```

Examples from the tutorial in GO official page:
```bash
package main

import "fmt"

func main() {
	fmt.Println("Hello, 世界")
}
```

Every Go program is made up of packages.
Programs start running in package main.
This program is using the packages with import paths "fmt" and "math/rand".
```go
package main

import (
	"fmt"
	"math/rand"
)

func main() {
	fmt.Println("My favorite number is", rand.Intn(10))
}
```

By convention, the package name is the same as the last element of the import path. For instance, the "math/rand" package comprises files that begin with the statement package rand.

So similar to the game that was used in the test algorithm exercise there is the main package that executes everything, and you can import additional packages. Similar to python in that sense

Seems like fmt package is needed for printing and math/rand is used for random number generator

2 ways of importing:
```go
import (
	"fmt"
	"math"
)
```

or
```go
import "fmt"
import "math"
```

Packages seem to start with small letters, but the functions inside it (like Pi inside math can only start with Capital letters)
So rand.Intn and math.PI are the way to go
Capital letter names are exported names
"When importing a package, you can refer only to its exported names. Any "unexported" names are not accessible from outside the package" ~ which I think means that the package main only uses small letters for local packages and everything that's imported has to be caputal letter

A function can take zero or more arguments.
```go
package main

import "fmt"

func add(x int, y int) int {
	return x + y
}

func main() {
	fmt.Println(add(42, 13))
}
```

Types in GO:
- int = integer
- string = string
- bool = boolean

### Types
The type of arguments comes after the arguments. The type of the output comes after the func(). A function can return any number of results. if the output is multiple then you can define types in ()
```go
func swap(x, y int) (int, int) {
	return y, x
}
```

multiple outputs:
```go
func swap(x, y int) (int, int) {
	return y, x
}

func main() {
	a, b := swap(1, 2)
	fmt.Println(a, b)
}
```

When two or more consecutive named function parameters share a type, you can omit the type from all but the last. Note that naming a variable like this can only happen inside a function

In this example, we shortened

```go
x int, y int
```

to
```go
x, y int
```

Types:
- bool
- string
- int  int8  int16  int32  int64 # can ignore anything other than int for now
- uint uint8 uint16 uint32 uint64 uintptr  # can ignore everything in this row
- byte // alias for uint8
- rune // alias for int32 & represents a Unicode code point # can ignore everything in this row
- float32 float64 # use 64 bits given your computer is 64 bits
- complex64 complex128 # use 64 bits given your computer is 64 bits

When you need an integer value you should use **int** unless you have a specific reason to use a sized or unsigned integer type.

The example shows variables of several types, and also that variable declarations may be "factored" into blocks, as with import statements.
```go
package main

import (
	"fmt"
	"math/cmplx"
)

var (
	ToBe   bool       = false
	MaxInt uint64     = 1<<64 - 1
	z      complex128 = cmplx.Sqrt(-5 + 12i)
)

func main() {
	fmt.Printf("Type: %T Value: %v\n", ToBe, ToBe)
	fmt.Printf("Type: %T Value: %v\n", MaxInt, MaxInt)
	fmt.Printf("Type: %T Value: %v\n", z, z)
}
```
Output:
Type: bool Value: false
Type: uint64 Value: 18446744073709551615
Type: complex128 Value: (2+3i)
#### I didn't understand this code yet

To convert between types:
```go
func main() {
	var x, y int = 3, 4
	var f float64 = math.Sqrt(float64(x*x + y*y))
	var z uint = uint(f)
	fmt.Println(x, y, z)
}
```

### Return

A return statement without arguments returns the named return values. This is known as a "naked" return.
Naked return statements should be used only in short functions, as with the example shown here. They can harm readability in longer functions.
```go
func split(sum int) (x, y, z int) {
	x = sum * 4 / 9
	y = sum - x
	z = 123456789
	return
}

func main() {
	fmt.Println(split(17))
}
```

### Declarations: Var statement and initializing

The var statement declares a list of variables of 1 type; as in function argument lists, the type is last.

A var statement can be at package or function level. We see both in this example.
```go
var c, python, java bool

func main() {
	var i int
	fmt.Println(i, c, python, java)
}
```
The return will be: 0 false false false because when declaring it sets the default value. 0 for int and false for boolean

Declaring is optional because it can take the type of the initializer. also when using initializer it can overwrite the initial value but it has to stay the same type. to change type you need to set the type again with a complete satement var j int = 1 (if you want to make a integer)
var i, j int = 1, 2

func main() {
	fmt.Println(i, j)
	var c, python, java, i, j = true, false, "no!", 12,13
	fmt.Println(i, j, c, python, java)
}

Inside a function, the := short assignment statement can be used in place of a var declaration with implicit type.
Outside a function, every statement begins with a keyword (var, func, and so on) and so the := construct is not available.
```go
func main() {
	var i, j int = 1, 2
	k := 3
	c, python, java := true, false, "no!"

	fmt.Println(i, j, k, c, python, java)
}
```

### Constants:
Constants are declared like variables, but with the const keyword.

Constants can be character, string, boolean, or numeric values.

Constants cannot be declared using the := syntax.
```go
package main

import "fmt"

const Pi = 3.14

func main() {
	const World = "世界"
	fmt.Println("Hello", World)
	fmt.Println("Happy", Pi, "Day")

	const Truth = true
	fmt.Println("Go rules?", Truth)
}
```

Currently working through https://go.dev/tour/list at step 16 of Packages, Variables, and Functions of Basics. I didn't understand what numeric constants are but I don't think it's that necesary\. So I'm done with the first part of the tutorial.
For, if, else, defer and switch statements should be fairly understandable (Section 2). I will go through that quickly later and then I would need to watch the videos provided in the school platform to set up my computer to complete tasks. Aside from the knowledge I have I don't think I need to much extra info. The question is whether I would be able to finish that by tomorrow 10AM

### Loops and constructs:
Basics of for loops:
```go
for i := 0; i < 10; i++ {
	sum += i
}
```
3 parts separated by semicolons:
init statement (variable declaration, only used in the loop): for i := 0 - executed before the first iteration
**condition expression**: i < 10 - evaluated before each iteration
post statement:  i++  - executed at the end of each iteratopm
Braces contain the action to be done in the loop - sum += 1
Init and ost statements are optional if you declared the variable to be looping over earlier; and the action to be done after each loop inside the loop; however you have to keep both semicolos (;) before and after condition expression or you can drope both of them (either both are present or 0)
But without condition expression the loop would be infinite and that's not good

**Same for if statements** They can also contain return statement if the if is located inside a functiob
```go
if x < 0 {
	return sqrt(-x) + "i"
}
```
You can include the short init statement; the variable would only be used inside the if statement and inside its else statement
```go
	z := 5
	if z < 3 {
		fmt.Println(z)
	} else {
		fmt.Printf(">3")
	}
```
### switch 
switch statement is a short way to write if else statement

### defer
defer statement defers executaion of a function intil the surrounding function returns (everything in it finishes); multiple defer calls stacl and are executed last in first out order (the ones that came last would be executed first)

### fmt
Println - prints integers
Printf - prints strings and combined 
