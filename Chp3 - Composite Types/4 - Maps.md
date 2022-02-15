# Maps

Go provides a built-in type for situations where you want to associate one value with another. The map type is written as `map[keyType]valueType`.

```go
var nilMap map[string]int // nil with 0 length, you can't write on a nil map

emptyMap := map[string]int{} // empty map with length 0 but you can read and write on it.
```

In the above scenario we created a map with `strings` keys and `int` values.

A map literal's body is written as the key, followed by a colon, then the value; There's a comma separating each key-value pair in the map, **even** on the last line.

```go
teams := map[string][]string {
    "Orcas": []string{"Fred", "Ralph", "Bijou"},
    "Lions": []string{"Sarah", "Peter", "Billie"},
    "Kittens": []string{"Waldo", "Raul", "Ze"},
}
```

If you happen to know the amount of key-value pair you intend to put in the map, you can use `make` to create a map with a default size.

```go
ages := make(map[int][]string, 10)
```

Maps are like slices in the following ways.

- Maps automatically grow as one adds key-value pairs to them.
- If you know how make key-value pairs you plan to insert in a map, you can use the `make` function with a specific initial size.
- Passing a map to the `len` function tells you the number of key-value pairs in the map.
- The zero value for a map is `nil`.
- Maps are not comparable. You can check if they are equal to nil, but you can not check if two maps are equal or different with the `==` or `!=` operators. 

The key for a map can be any **comparable type**. This means that we cannot use a slice or a map as the key for a map.

The map implemented in Go is a **hash map**.

## Writing and reading a Map

We assign a value to a map key by putting the key within brackets and using `=` to specify the value, and we read the value assigned to a map key by putting the key within brackets. 

When trying to read the value assigned to a map key that never was set the map returns the zero value for the map's value type.

```go
totalWins := map[string]int{}
totalWins["Orcas"] = 1
totalWins["Lions"] = 2
fmt.Println(totalWins["Orcas"])
fmt.Println(totalWins["Kittens"])

totalWins["Kittens"]++
fmt.Println(totalWins["Kittens"])

totalWins["Lions"] = 3
fmt.Println(totalWins["Lions"])
```

## The comma ok idiom

Sometimes we need to check if a key is in a map, and for that Go provides the `comma ok idiom` to tell the difference between a key that's associated with a zero value and a key that's not in the map.

```go
m := map[string]int{
    "hello": 5,
    "world": 0,
}

v, ok := m["hello"]
fmt.Println(v, ok)

v, ok = m["world"]
fmt.Println(v, ok)

v, ok = m["goodbye"]
fmt.Println(v, ok)
```

With this approach we get two results back, the first one is the value (if any) within that key and the second one is a boolean that tells us `true` if the key is present in the map and `false` if otherwise.

## Deleting from maps

Key-value pairs are removed form a map via the built-in `delete` function.

```go
m := map[string]int{
    "hello": 5,
    "world": 10,
}

delete(m, "hello")
```

This function takes a map and a key and then removes the key-value pair with the specified key. If the key's not present in the map or the map is `nil`, nothing happens. The `delete` function does not return any value.

## Using maps as Sets

Go does not provide any `set` data type in the standard library, but it can be simulated with a `map` or `struct`.

I won't cover this simulation here, I just wanted to note that it is possible to somewhat simulate `Sets` in Go.
