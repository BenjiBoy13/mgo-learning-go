# goto. Yes, goto

Yes, Go has a `goto` statement, it is recommended to avoid the use of it because of the confusion it may cause, but it does have some uses.

In Go, a goto statement specifies a labeled line of code and execution jumps to it. However, we can’t jump anywhere. Go forbids jumps that skip over variable declarations and jumps that go into an inner or parallel block.

```go
func main() {
    a := rand.Intn(10)
    
    for a < 100 {
        if a % 5 == 0 {
            goto done
        }
    
        a = a*2 + 1
    }
    
    fmt.Println("do something when the loop completes normally")
    
    done:
        fmt.Println("do complicated stuff no matter why we left the loop")
        fmt.Println(a)
}
```
The example above may be one of the few use cases in which the `goto` statement is actually the best option, since it improves code readability.

