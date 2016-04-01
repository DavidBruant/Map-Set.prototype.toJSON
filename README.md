# Map-Set.prototype.toJSON

An [ECMAScript](https://github.com/tc39/ecma262) proposal. ~~Currently at **Stage 0**.~~

This proposal was brought before the committee in the March 2016 meeting, and thoroughly rejected. [Details](https://github.com/DavidBruant/Map-Set.prototype.toJSON/issues/16)

## Problem

Here is the current situation:

````js
var s = new Set(['yo', 'ya', true, 8]);

console.log(JSON.stringify(s)); // '{}'
````

This result is unhelpful. Same goes for Map.


## Proposal

This proposal is about providing a sensible default to the common operation of JSON serialization via default `toJSON` implementations on `Set.prototype` and `Map.prototype`. Of course, userland code can always shadow this value on specific instances.

### Map.prototype.toJSON

The essence of the proposal is captured in this snippet (spec in [markdown](spec.md#mapprototypetojson--) or [HTML](http://davidbruant.github.io/Map-Set.prototype.toJSON/#Map.prototype.toJSON)):

````js
Map.prototype.toJSON = function toJSON() {
  return [...Map.prototype.entries.call(this)];
}
````

### Set.prototype.toJSON

The essence of the proposal is captured in this snippet (spec in [markdown](spec.md#setprototypetojson--) or [HTML](http://davidbruant.github.io/Map-Set.prototype.toJSON/#Set.prototype.toJSON)):

````js
Set.prototype.toJSON = function toJSON() {
  return [...Set.prototype.values.call(this)];
}
````

## Discussion

There might be a web compat concern if code using native Map and Set or polyfill relies on the current JSON.stringify behavior.


# Licence

This work is dedicated to the public domain. It is [CC0 licenced](https://creativecommons.org/publicdomain/zero/1.0/).
