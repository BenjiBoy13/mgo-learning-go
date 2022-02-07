# Naming variables and constants 

Go requires identifier names to start with a letter or underscore, the names can contain numbers, underscores and letters.; Go uses camel case when an identifier consists of multiple words.

```go
var _validName int = 0 // Legal
var $var int = 2 // Legal
var 2d int = 0 // Ilegal

var simpleVariable int = 0 // Do this
var simple_vairble_2 int = 0 // Do not do this.
```

As a recommendation in go, the names of the variables inside a function should be rather small and not so descriptive, in the other hand, variables at the package level should be named with more descriptive names since their use is wider.
