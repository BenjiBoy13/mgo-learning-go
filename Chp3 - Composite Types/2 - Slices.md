# Slices

The main difference between a Go array and a Slice is that slices don't take the length is not part of the type, meaning, they can be of any size and grow if needed.

```go
var x = []int{1, 2, 3} // <-- Slice
var y = [...]int{1, 2, 3} // <-- Array
```

As with arrays we can simulate multidimensional slices, and we can also specify the values of specific indexes in the slice. 

```go
var x = []int{1: 10, 100: 9}
var y = [][]int 
```

We can also declare a variable of type slice without specifying values and the main difference is that the zero value of a slice is `nil` which is similar to `null` in other languages, in Go, `nil` means that a type is lacking a value.

Another difference with arrays is that we can not compare slices using the `==` or `!=` operators, the only thing we can compare a slice to is with `nil`.

## Built-in slice functions

### len

`len` works pretty much the same as with arrays, it returns the length of the slice, if the slice is `nil` it will return 0.

### append

The `append` function takes at least two parameters, a slice of any type and a value of that type and returns a slice of the same type with the appended value.

```go
var x []int
x = append(x, 10)

var y = []int{1, 2, 3}
y = append(y, 10)
```

We can append more than one value at a time; And we can also append another slice of the same type using the `...` operator that basically separates the values of the slice.

```go
var x []int
x = append(x, 1, 2, 3)

var y = []int{4, 5, 6}
x = append(x, y...) 
```

*Important note with `append`: It's a compile error to not assign the returned value of the append function to a variable.*

### cap

It is important to mention that every slice has a capacity (number of memory locations reserved) and each time we append to a slice and the slice is at capacity the Go runtime will create a new slice with a higher capacity and copy the values to the new slice and then return it: Since this process takes some time, when the slice hits its capacity Go will create the new slice and double the capacity when the length of the slice is less than or equal to 1024 otherwise it will expand the capacity on a 25%.

Hence, the `cap` built-in function returns the current capacity of the slice.

```go
var x []int
x = append(x, 1, 2, 3, 4, 5, 6)
c := cap(x)
fmt.Println(x, c) // <-- 6

x = append(x, 1, 2)
c = cap(x)
fmt.Println(x, c) // <-- 12
```

### make

While it is cool that slices grow automatically, it is more efficient to create a slice with a specific capacity out of the box, and we can do this with the `make` function.

The `make` function is the third way in which we can declare a slice variable, it allows to create a slice specifying the type, length (we can always grow it, it is not limited) and capacity (if we want to).

```go
x := make([]int, 5) // x[0] = 0... x[4] = 0; Capacity: 5
y := make([]int, 5, 10) // x[0] = 0... x[4] = 0; Capacity: 10
```

*Important note: Never specify a capacity that is less than the length of the slice.*

### copy

Go offers the built-in `copy` function to creat an independent slice of the original.

```go
x := []int{1, 2, 3, 4}
y := make([]int, 4)
num := copy(y, x)

/*
y: [1 2 3 4]
num: 4
*/

z := make([]int, 2)
num2 := copy(z, x)

/*
z: [1 2]
num2: 2
*/
```

As you can see the function takes 2 parameters, the first one is the destination and the second is the source slice. It copies as many values as it can from source to destination, limited by whichever slice is smaller, and returns the number of elements copied.

The copy function also accepts as parameters *slice expressions* (explained in the following topic).

```go
x := []int{1, 2, 3, 4}
y := make([]int, 2)
copy(y, x[2:])

/*
y := [3 4]
*/
```

## Slicing slices

A *slice expression* creates a slice from a slice. It's written inside of brackets that consists of a starting and ending offset, separated by a colon: When you leave off the starting offset, 0 is assumed. Likewise, if you leave off the ending offset, the end of the slice is substituted.

```go
x := []int{1, 2, 3, 4}
y := x[:2] // [1 2]
z := x[1:] // [2 , 3, 4] 
d := x[1:3] // [2 3]
e := x[:] // [1 2 3 4]
```

### Slices share storage sometimes

When taking a slice from a slice we are **not copying**: instead, we are creating 2 variables that share memory, meaning that a change to an element in a slice affect all slices that share that element.

```go
x := []int{1, 2, 3, 4}
y := x[:2] // [1 2]
z := x[1:] // [2, 3, 4] 

x[1] = 20
y[0] = 10
z[1] = 30

/*
x: [10 20 30 4]
y: [10 20]
z: [20 30 4]
*/
```

In Go it is possible to use the `append` built-in function with slices which means that overlapping may occur between the subslices; Another important thing to mention is that subslices take the capacity of the original slice. 

```go
x := []int{1, 2, 3, 4} // [1 2 3 4]
y := x[:2] // [1 2]
y = append(y, 30)

/*
x: [1 2 30 4]
y: [1 2 30]
*/
```

As we can see things start to get pretty confusing when we start manipulating subslices this is why it is recommended to either don't use `append` on subslices or use the full slice expression.

The full slice expression contains a third number separated by a colon that indicates the last position in the parent slice's capacity that's available for the subslice, this protects us aggains the `append`.

```go
x := make([]int, 0, 5)
x = append(x, 1, 2, 3, 4)
y := x[:2:2]
z := x[2:4:4]
```

Utterly confusing.

## Converting arrays into slices

Slices are not the only thing we can slice, Go also enables us to slice an array which is very useful to bridge the array restrictions but slicing from an array is not different that slice, meaning, they would also share memory.

```go
x := [4]int{5, 6, 7, 8}
y := x[:2]
z := x[2:]
x[0] = 10

/*
x: [10 6 7 8]
y: [10 6]
z: [7 8]
*/
```

