# Avoid Ambiguity 

**Include all the words needed to avoid ambiguity** for a person
reading code where the name is used.

✅ For example, consider a method that removes the element at a
given position within a collection.

``` swift
extension List {
public mutating func remove(at position: Index) -> Element
}
employees.remove(at: x)
```

⛔ If we were to omit the word `at` from the method signature, it could
imply to the reader that the method searches for and removes an
element equal to `x`, rather than using `x` to indicate the
position of the element to remove.

``` swift
employees.remove(x) // unclear: are we removing x?
```

