# Map-Set.prototype.toJSON

An [ECMAScript](https://github.com/tc39/ecma262) proposal. Currently at **Stage 0**.


## Problem

Here is the current situation:

````js
var s = new Set(['yo', 'ya', true, 8]);

console.log(JSON.stringify(s)); // '{}'
````

This result is unhelpful. Same goes for Map.


## Proposal

This proposal is about providing a sensitive default to the common operation of JSON serialization via default `toJSON` implementations on `Set.prototype` and `Map.prototype`. Of course, userland code can always shadow this value on specific instances.

### Map.prototype.toJSON

For now in JS (instead of in spec prose), the essence of the proposal is captured in this snippet:

````js
Map.prototype.toJSON = function(){
  var o = Object.create(null); // to avoid __proto__ nonsense
  for(let [key, value] of this.entries()){
    o[k] = v;
  }
  return o;
}
````

### Set.prototype.toJSON

Same as above.

````js
Set.prototype.toJSON = function(){
  return [...this];
}
````

## Discussion

There might be a web compat concern if code using native Map and Set or polyfill relies on the current JSON.stringify behavior.


