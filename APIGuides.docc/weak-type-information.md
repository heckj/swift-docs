# Compensate for weak type information

**Compensate for weak type information** to clarify a parameter's role.

Especially when a parameter type is `NSObject`, `Any`, `AnyObject`, or a fundamental type such as `Int` or `String`, type information and context at the point of use may not fully convey intent. 
In this example, the declaration may be clear, but the use site is vague.

⛔

``` swift
func add(_ observer: NSObject, for keyPath: String)

grid.add(self, for: graphics) // vague
```

✅ To restore clarity, **precede each weakly typed parameter with a noun describing its role**:

``` swift
func add**Observer**(_ observer: NSObject, for**KeyPath** path: String)
grid.addObserver(self, forKeyPath: graphics) // clear
```
