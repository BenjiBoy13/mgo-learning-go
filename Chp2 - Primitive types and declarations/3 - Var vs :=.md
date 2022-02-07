# Var Vs := 

## var

The most verbose way to declare a variable in GO is with the `var` keyword, an explicit type and an assignment; If we do not assign a value it will take it's zero value.

```go
var x int32 = 10  
var y int32  // y = 0
var z string // z = ''
```

If we do not explicitly specify the type it will take the form of the literal default, in the following case, an `int`

```go
var x = 10 // int
```

We can also declare multiple variables at once with `var`.

```go
var x, y int = 10, 100
var w, z int // w = 0; z = 0
var a, b = 10, "Hello"
```

Another alternative is to wrap the variables in a declaration list.

```go
var (
	x		int
	y				= 20
	z		int 	= 30
	d, e			= 40, "Hello"
	f, g	string
)
```

## :=

Go supports a short declaration format with the keyword `:=`. When you are **inside** a function, you can use the `:=` operator to replace the `var` declaration that uses type inference.

```go
// ...
// Inside a function
var x = 10 
y := 10

var w, z = 10, "Hello"
a, b := 10, "Hello"
// ...
```

Remember: `:=` is **not** legal outside a function. 

Situations within functions when it's advised to avoid `:=`
1. When initializing a variable to it's zero value.
2. When assigning an untyped constant or literal to a variable and the default type is not the desired type.
3. Since `:=` allows you to assign to both new and existing variables, it sometimes creates new variables when thinking you are 're-using' existing ones. Explicitly declare new variables with `var` to  make it clear.











