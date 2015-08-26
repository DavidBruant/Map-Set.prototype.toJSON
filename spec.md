# Map.prototype.toJSON ( )

This function provides an Array representation of a Map object for use by `JSON-stringify`.

When the **toJSON** method is called, the following steps are taken:

1. Let *M* be the **this** value.
1. Let *entries* be CreateMapIterator(*M*, **"key+value"**)
1. ReturnIfAbrupt(*entries*).
1. Let *A* be ArrayCreate(**0**).
1. ReturnIfAbrupt(*A*).
1. Let *k* be **0**.
1. Repeat
  1. Let *Pk* be ToString(*k*).
  1. Let *next* be IteratorStep(*entries*).
  1. ReturnIfAbrupt(*next*).
  1. If *next* is **false**, then
    1. Let *setStatus* be Set(*A*, "length", *k*, **true**).
    1. ReturnIfAbrupt(*setStatus*).
    1. Return *A*.
  1. Let *nextValue* be IteratorValue(*next*).
  1. ReturnIfAbrupt(*nextValue*).
  1. Let *defineStatus* be CreateDataPropertyOrThrow(*A*, *Pk*, *nextValue*).
  1. If *defineStatus* is an abrupt completion, return IteratorClose(*entries*, *defineStatus*).
  1. Increase *k* by 1.

The `length` property of the `toJSON` method is **0**.

# Set.prototype.toJSON ( )

This function provides an Array representation of a Map object for use by `JSON-stringify`.

When the **toJSON** method is called, the following steps are taken:

1. Let *S* be the **this** value.
1. Let *values* be CreateSetIterator(*S*, **"value"**)
1. ReturnIfAbrupt(*values*).
1. Let *A* be ArrayCreate(**0**).
1. ReturnIfAbrupt(*A*).
1. Let *k* be **0**.
1. Repeat
  1. Let *Pk* be ToString(*k*).
  1. Let *next* be IteratorStep(*values*).
  1. ReturnIfAbrupt(*next*).
  1. If *next* is **false**, then
    1. Let *setStatus* be Set(*A*, "length", *k*, **true**).
    1. ReturnIfAbrupt(*setStatus*).
    1. Return *A*.
  1. Let *nextValue* be IteratorValue(*next*).
  1. ReturnIfAbrupt(*nextValue*).
  1. Let *defineStatus* be CreateDataPropertyOrThrow(*A*, *Pk*, *nextValue*).
  1. If *defineStatus* is an abrupt completion, return IteratorClose(*values*, *defineStatus*).
  1. Increase *k* by 1.

The `length` property of the `toJSON` method is **0**.
