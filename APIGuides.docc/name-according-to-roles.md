# Name according to roles

**Name variables, parameters, and associated types according to their roles,** rather than their type constraints.


⛔ 

``` swift
var **string** = "Hello"
protocol ViewController {
  associatedtype **View**Type : View
}
class ProductionLine {
  func restock(from **widgetFactory**: WidgetFactory)
}
```

✅ Repurposing a type name in this way fails to optimize clarity and
expressivity. Instead, strive to choose a name that expresses the
entity's *role*.


``` swift
var **greeting** = "Hello"
protocol ViewController {
  associatedtype **ContentView** : View
}
class ProductionLine {
  func restock(from **supplier**: WidgetFactory)
}
```

✅ If an associated type is so tightly bound to its protocol constraint
that the protocol name *is* the role, avoid collision by appending
`Protocol` to the protocol name:

``` swift
protocol Sequence {
  associatedtype Iterator : Iterator**Protocol**
}
protocol Iterator**Protocol** { ... }
```
