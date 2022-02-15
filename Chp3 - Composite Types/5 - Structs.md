# Structs

When we have related data that needs to be grouped together we use `structs`.

```go
type person struct {
    name string
    age int
    pet string
}
```

A `struct` type is defined by the keyword `type`, the name of the `struct` type, the keyword `struct` and a pair of braces. Within the braces, you list fields in the `struct`, which unlike map literals, there are no commas separating the field in the declaration. We can define structs inside or outside functions, but keep in mind that structs defined in a function cannot be used outside them.

Once a struct is defined we can use it to define variables; The zero value for structs is the zero of all the fields.

```go
var p person
p2 := person{}
```

A struct literal can be specified in two different ways but you cannot mix them.

```go
p := person{
    "Julia",
    40,
    "cat",
}

p2 := {
    age: 30,
    name: "Beth",
}
```
A field in a struct can be accessed with dotted notation.

```go
p.name = "Bob"
fmt.Println(p2.name)
```

## Anonymous Structs

We can also declare that a variable implements a struct type without giving the struct a name. This is called an `anonymous struct`.

```go
pet := struct {
    name string
    kind string
}{
    name: "Fido".
    kind: "Dog"
}
```

## Comparing and converting structs

Whether a struct is comparable or not depends on the struct's fields. Structs that are entirely composed out of comparable types are comparable; those with slices, maps, function or channel fields (will be seen later) make the struct incomparable.

Just like Go doesn't allow comparison between variables of different primitive types, Go does not allow comparison between variables that represent structs of different types.

Go does allow you to perform a type conversion from one struct to another if the fields of both structs have the same names, order, and types.

Let us review an example.   

```go
type firstPerson struct {
    name string
    age int
}

type secondPerson struct {
    name string
    age int
}
```

We can use a type conversion to convert an instance of `firstPerson` to `secondPerson`, but we can't use `==` to compare an instance of `firstPerson` and an instance of `secondPerson`, because they are different types. 

Anonymous structs act a bit different, if two struct variables are being compared and at least one of them is an anonymous struct, we can compare them without a type conversion if the fields of both structs have the same name, order and types; We can also assign between named and anonymous struct types if the fields of both structs have the same names, order and types.

```go
type firstPerson struct {
    name string
    age int
}
f := firstPerson{
    name: "Bob",
    age: 50,
}

var g struct {
    name string
    age int
}

g = f
fmt.Println(f == g)
```

The previous code compiles because we can use `=` and `==` between identical named and anonymous structs.



