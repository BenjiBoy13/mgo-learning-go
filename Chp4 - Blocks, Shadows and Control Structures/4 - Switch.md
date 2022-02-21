# Switch

Like many c-derived languages, Go offers a `switch` logic statement.

```go
words := []string{
        "a", "cow", "smile", "gopher", "octopus", "anthropologist" 
}

for _, word := range words {
    switch size := len(word); size {
        case 1, 2, 3, 4:
            fmt.Println(word, "is a short word!")
        case 5:
            wordLen := len(word)
            fmt.Println(word, "is exactly the right length:",wordLen)
        case 6, 7, 8, 9:
        default:
            fmt.Println(word, "is a long word!")
    }
}

/*
    Output
    a is a short word!
    cow is a short word!
    smile is exactly the right length: 5
    anthropologist is a long word!
*/
```

Just like the `if` statements in Go, we don't put parenthesis around the value being compared in the switch, and we can declare variables in the switch declaration.

An important difference that we find with other c-derived languages is that in Go, we don't need to use the `break` keyword at the end of every case since the switch statements in Go don't fall through. Another important point to make is that when we don't define any logic inside a case then nothing happens.

We can `switch` over any comparable type; In other words, if we can use the `==` operator on the type we can use `switch` on it.

Now, we can use the `break` keyword in `switch` statements in case we want to exist the `switch` prematurely in a clause or we if the `switch` is inside a labeled loop we can exit the loop with the `break` keyword followed by the label of the `for`.

## Blank Switches

A regular `switch` only allows us to check a value for equality but a blank `switch` allows you to use any boolean comparison for each case. 

```go
words := []string{"hi", "salutations", "hello"}
for _, word := range words {
    switch wordLen := len(word); {
        case wordLen < 5:
            fmt.Println(word, "is a short word!")
        case wordLen > 10:
            fmt.Println(word, "is a long word!")
        default:
            fmt.Println(word, "is exactly the right length.")
    }
}

/*
    Output
    hi is a short word!
    salutations is a long word!
    hello is exactly the right length.
*/
```


