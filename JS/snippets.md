# Snippets

## Object copy function
*Origin Link: <https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/forEach>*

```js
function copy(obj) {
  var copy = Object.create(Object.getPrototypeOf(obj));
  var propNames = Object.getOwnPropertyNames(obj);

  propNames.forEach(function(name) {
    var desc = Object.getOwnPropertyDescriptor(obj, name);
    Object.defineProperty(copy, name, desc);
  });

  return copy;
}

var obj1 = { a: 1, b: 2 };
var obj2 = copy(obj1); // obj2 looks like obj1 now

```

## Object extend function & Ojbect merge function

```js
function extend(dest, src) {
    for (var key in src) {
        if (src.hasOwnProperty(key)) dest[key] = src[key]
    }
    return dest
}
```

```js
function merge(obj1,obj2){
    var obj3 = {}
    for (var attrname in obj1) { obj3[attrname] = obj1[attrname] }
    for (var attrname in obj2) { obj3[attrname] = obj2[attrname] }
    return obj3
}
```

## Make hash value

```js
const makeHash = str => str.split('').reduce((hash, char) => (hash << 5) - hash + char.charCodeAt(), 0)
```
