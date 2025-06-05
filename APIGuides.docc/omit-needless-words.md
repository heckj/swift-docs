# Omit needless words 

Every word in a name should convey salient information at the use site.

More words may be needed to clarify intent or disambiguate meaning, but those that are redundant with information the reader already possesses should be omitted. 
In particular, omit words that *merely repeat* type information.

⛔ In this case, the word `Element` adds nothing salient at the call site:

``` swift
public mutating func removeElement(_ member: Element) -> Element?

allViews.removeElement(cancelButton)
```

✅ This API would be better:

``` swift
public mutating func remove(_ member: Element) -> Element?

allViews.remove(cancelButton) // clearer
```

Occasionally, repeating type information is necessary to avoid ambiguity, but in general it is better to use a word that describes a parameter's *role* rather than its type. 
See <doc:name-according-to-roles> for details.
