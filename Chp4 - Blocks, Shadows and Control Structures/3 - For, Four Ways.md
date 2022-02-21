# For, Four Ways

Just like any other language in the C family, Go uses a `for` statement to loop; What makes it different from others is that the `for` keyword is the **only** way we can loop, and for that, Go provides 4 different formats.

1. A complete, C-style for
2. A condition-only for
3. An infinite for
4. for-range

## The four ways

### The complete for statement

This format of the `for` keyword is pretty similar to the one in the C language with the same exception as with the `if` statement, there's no parenthesis containing the condition.

```go
for i := 0; i < 10; i++ {
    fmt.Println(i)
}
```

There are just 2 important details about this format, one, the variables declared in the for loop condition can shadow variables in the containing block and second, we **can not** use the `var` keyword to initialize variables in the loop condition.

### The condition-only statement

Go allows us to leave off both, the initialization and the increment in the `for` statement. That leaves us with a `for` that acts like a `while` in other languages.

```go
i := 1
for i < 10 {
    fmt.Println(i)
    i += 1
}
```
### The infinite for statement

Go also allows to declare a `for` without declaring any condition at all, creating an endless loop.

```go
func main() {
    for {
        fmt.Println("Hello")
    }
}
```

#### Break and continue

Just like most languages, Go implements the `continue` and `break` keywords to get out of a loop (any loop) with `break`, and to stop the cycle of the loop at some point and continue with the next one with `continue` 

### The for-range statement

The fourth format is used to iterate over elements in some Go's built-in types. The `for-range` loop resembles the iterators found on other languages.

```go
evenVals := []int{2, 4, 6, 8, 10, 12}

for i, v := range evenVals {
    fmt.Println(i, v)
}

/*
    Output: 
    0 2
    1 4
    2 6
    3 8
    4 10
    5 12
*/
```

The interesting part of a `for-range` is that we get two loop variables. The first one is the position in the data structure being iterated, while the second one is the value at that position.

The idiomatic names for the looped variables depend on the data structure being looped over; When looping over an array, slice or string we commonly use the `i` for index and `v` for value, when looping over a map we use the `k` for key and `v` for value.

It is important to remember that it is a **compiler error** if we declare unused variables, therefore, if we don't need the index or key part of a for-range loop we can use the `_` key to make Go ignore that value.

```go
evenVals := []int{2, 4, 6, 8, 10, 12}

for _, v := range evenVals {
    fmt.Println(v)
}

/*
    Output:
    2
    4
    6
    8
    10
    12
*/
```

When we don't want to use the value we can either use the `_` or remove it from the declaration.

```go
uniqueNames := map[string]bool{
    "Fred": true, "Raul": true
}

for k := range uniqueNames {
    fmt.Println(k)
}
```

## Iteration over map

It is important to mention that Go implements a security feature with maps to prevent Hash DoS attacks. They accomplished that by modifying the hash function inside the map implementation to change the default ascending order of the iteration with some random order when iterating over the same map multiple times; Creating results such as:

```go
m := map[string]int{
    "a": 1,
    "c": 3,
    "b": 2,
}

for i := 0; i < 3; i++ {
    fmt.Println("Loop", i)
    
    for k, v := range m {
        fmt.Println(k, v)
    }
}

/*
    Outputs
    Loop 0
    c 3
    b 2 
    a 1

    Loop 1
    a 1
    c 3
    b 2

    Loop 2
    b 2
    a 1
    c 3
*/
```

### Iterating over strings

When Go iterates over a string it separates the string into runes, **not bytes**, whenever a for-range loop encounters a multi-byte rune in a string, it converts the UTF-8 representation into a single 32-bit number and assigns it to the value. The offset is incremented by the number of bytes in the rune.

```go
samples := []string{"hello", "apple_π!"}

for _, sample := range samples {

    for i, r := range sample {
        fmt.Println(i, r, string(r))
    }

    fmt.Println()
}

/*
    Output
    0 104 h
    1 101 e
    2 108 l
    3 108 l
    4 111 0

    0 97 a
    1 112 p
    2 112 p
    3 108 l
    4 101 e
    5 95 _
    6 960 π
    8 33 !
*/
```

## The for-range value is a copy

Each time the for-range loop iterates over a compound type, it copies the value from the compound type to the value variable. **Modifying the value variable will not modify the value in the compound type**.

```go
evenVals := []int{2, 4, 6, 8, 10, 12}

for _, v := range evenVals {
    v *= 2
}

fmt.Println(evenVals) // [2 4 6 8 10 12]
```

## Labeling the "for" statements

When we have nested loops and want to use the `continue` or `break` keywords we find ourselves in a difficult situation since those keywords will get us out of the inner for in which they are used, in Go we can break or continue out of an outer for loop by using something like this: 

```go
func main() {
    samples := []string{"hello", "apple_π!"}
    outer:
        for _, sample := range samples {
            for i, r := range sample {
                fmt.Println(i, r, string(r))
                
                if r == 'l' {
                    continue outer
                }
            }
        
        fmt.Println()
        }
}
```










