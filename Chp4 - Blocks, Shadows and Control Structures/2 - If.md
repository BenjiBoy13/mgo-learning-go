# If

The `if` statement in Go is pretty much the same as in other languages with the exception that they don't use parenthesis to capsule the logical part.

```go
n := rand.Intn(10)
if n == 0 {
    fmt.Println("That'ss too low")
} else if n > 5 {
    fmt.Println("That's too big")
} else {
    fmt.Println("That's a good number")
}
```

As we discussed with blocks, every variable declared inside a `if` or `else` statement exists only within that block.

What Go adds to the table is the ability to declare variables that are scoped to the condition and the `if` and `else` block.

```go
if n := rand.Intn(10); n == 0 {
    fmt.Println("That'ss too low")
} else if n > 5 {
    fmt.Println("That's too big")
} else {
    fmt.Println("That's a good number")
}
```

Now, once the series of `if` and `else` statements ends, the `n` variable will become `undefined`.

