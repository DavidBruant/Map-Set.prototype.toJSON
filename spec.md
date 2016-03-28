# Map.prototype.toJSON ( )

This function provides an Array representation of an iterable object for use by [JSON.stringify][json-stringify] ([24.3.2][json-stringify]).

When the **toJSON** method is called, the following steps are taken:

1. Let *M* be the **this** value.
1. Let *iterator* be ? GetIterator(*M*)
1. Let *A* be ! ArrayCreate(**0**).
1. Let *k* be **0**.
1. Repeat
  1. Let *Pk* be ! ToString(*k*).
  1. Let *next* be ? IteratorStep(*iterator*).
  1. If *next* is **false**, then
    1. Perform ? Set(*A*, "length", *k*, **true**).
    1. Return *A*.
  1. Let *nextValue* be ? IteratorValue(*next*).
  1. Let *defineStatus* be CreateDataPropertyOrThrow(*A*, *Pk*, *nextValue*).
  1. If *defineStatus* is an abrupt completion, return IteratorClose(*iterator*, *defineStatus*).
  1. Increase *k* by 1.

The **length** property of the **toJSON** method is **0**.

# Set.prototype.toJSON ( )

The initial value of the **toJSON** property is the same function object as the initial value of the **Map.prototype.toJSON** property.

[json-stringify]: http://www.ecma-international.org/ecma-262/6.0/#sec-json.stringify
