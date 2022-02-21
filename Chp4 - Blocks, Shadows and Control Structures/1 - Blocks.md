# Blocks

Each place where a declaration occurs is called a `block`. 

Variable, constants, types and functions declared outside any functions are placed in the `package block`; All names in an import statement are in a `file block`.

All variables defined at the top level of a function (including the parameters of a function) are in a block. Within functions, we find the definition of another block and as we'll see later that inside every control structure there is another block. 

We can access an identifier defined in any outer block from within any inner block.

## Shadowing variables

A shadowing variable is a variable that has the same name as a variable in a containing block. For as long as the variable exists, you cannot access a shadowed variable.

```go
func main() {
	x := 10
	if x > 5 {
		fmt.Println(x) // 10

        /*
            Here we create a new variable with the same name 
            thus shadowing the top level x
        */
		x := 5 
		fmt.Println(x) // 5
	}
	fmt.Println(x) // 10
}
```

The above situation is one of the main reasons why we should be careful when using the `:=` operator, since that operator reuses variables that are declared in the current block, when using this operator we need to make sure we don't have any variables in the outer-scope with the same name unless our intention is to shadow them.

We also need to be careful to ensure that we are not shadowing a package import.

```go
import "fmt"

func main() {
	x := 10
	fmt.Println(x)

    /*
        Here we are shadowing the package fmt, making it 
        inaccesable in this block.
    */
	fmt := "oops"
	fmt.Println(fmt)
}
```

Won't compile: *fmt.Println undefined (type string has no field or method Println)*

Important note: Go does not include the built-in types, some built-in functions and `nil` in their keywords list, they are defined in a `universal block`, the block that contains all blocks described previously hence, it is possible to shadow names like `int`, `string`, etc. And the compiler and linter tools won't notice it, **we need to be careful, so we don't shadow any name in the universal block**.

As an example, here is a valid code.

```go
func main() {
	fmt.Println(true) // true
	true := 10 // <-- Shadowing the true type in the universal block 
	fmt.Println(true) // 10
}
```
