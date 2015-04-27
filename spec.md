# Map.prototype.toJSON ( )

This function provides an Array representation of a Map object for use by `JSON-stringify`.

When the **toJSON** method is called, the following steps are taken:

1. Let *M* be the **this** value.
1. Let *entries* be CreateMapIterator(*M*, **"key+value"**)
1. Return the result of evaluating `[...entries]`

The `length` property of the `toJSON` method is **0**.

# Set.prototype.toJSON ( )

This function provides an Array representation of a Map object for use by `JSON-stringify`.

When the **toJSON** method is called, the following steps are taken:

1. Let *S* be the **this** value.
1. Let *values* be CreateSetIterator(*S*, **"value"**)
1. Return the result of evaluating `[...values]`

The `length` property of the `toJSON` method is **0**.
