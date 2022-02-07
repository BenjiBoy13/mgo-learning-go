# Arrays

Like many other programming languages, Go has arrays, althought there are rarely use in Go.

## Declaration syntax and use

First and foremost, all elements in the array must be of the type specified, Go also needs to know the size of the array.

```go
var x [3]int
```

The previous example creates an array with 3 `int's` with all the positions initialized with the respective zero value; We can also specify the values with an array literal.

```go
var x [3]int{0, 1, 2} // x[0] = 0; x[1] = 2; x[2] = 2
var y = [3]int{5, 2: 5} // x[0] = 5; x[1] = 0; x[2] = 5
var z = [...]int{0, 0, 0} // x[0] = 0; x[1] = 0; x[2] = 0
```

We can use the `==` or `!=` operator to compare arrays.

```go
var x = [...]int{1, 2, 2}
var y = [3]int{1, 2, 3}
fmt.Println(x == y) // True
```

Go only has one dimensional arrays, we can simulate a multi-dimensional array but in reality we would be creating and array that holds arrays inside.

```go
var x[2][3]int 
```

The built-in function `len` takes an array and returns its length.

```go
var x int[3]
fmt.Println(len(x)) // 3
```
## Restrictions and reason of existence 

The reason why arrays are rarely used in Go is because of the following rules; Yet arrays are an important part of Go because they are used as a backing store for `slices` which is one of the most useful features of the language. 

- It's not possible to use a variable to specify the size of an array.
- It's not possible to use a type conversion to convert arrays of different sizes to identical types.
- It's not possible to write functions that work with arrays of any size.
- It's not possible to assign arrays of different sizes to the same variable. 

Arrays come into place when we are certain of it's size and type. 
