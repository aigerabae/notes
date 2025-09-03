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

### Var statement and initialazing

The var statement declares a list of variables; as in function argument lists, the type is last.

A var statement can be at package or function level. We see both in this example.
```go
var c, python, java bool

func main() {
	var i int
	fmt.Println(i, c, python, java)
}
```
The return will be: 0 false false false because when declaring it sets the default value. 0 for int and false for boolean

Declaring is optional because it can take the type of the initializer. also when using initializer it can overwrite the initial value but it has to stay the same type:
var i, j int = 1, 2

func main() {
	fmt.Println(i, j)
	var c, python, java, i, j = true, false, "no!", 12,13
	fmt.Println(i, j, c, python, java)
}
