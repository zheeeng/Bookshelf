# Parse URL

```js
function parseURL (url) {
  const patt = /^(\w+)\:\/\/([^\/]+)\/(.*)$/
  let [, protocol, fullhost, fullpath] = patt.exec(url)
  return [protocol, fullhost, fullpath, url]
}
```

# Get random color

```js
(~~(Math.random()*(1<<24))).toString(16)
```

# Computed object property names and destructuring

```js
let key = "z"
let { [key]: foo } = { z: "bar" }
```

# Get absolute URL

```js
var getAbsoluteUrl = (function () {
  var a

  return function (url) {
    if(!a) a = document.createElement('a')
    a.href = url

    return a.href
  }
})()
```

# Is element matches a specific selector

```js
function matchesSelector (el, selector) {
  var p = Element.prototype
  var f = p.matches || p.webkitMatchesSelector || p.mozMatchesSelector
    || p.msMatchesSelector || function (s) {
    return [].indexOf.call(document.querySelectorAll(s), this) !== -1
  }
  return f.call(el, selector)
}
```

# Manipulate DOM classes
The Element.classList is a read-only property which returns live DOMTokenList collection of the class attributes of the element.

**Syntax**

```js
var elementClasses = elementNodeReference.classList
```

**Methods**

* add( String [, String] )
* remove( String [,String] )
* item ( Number )
* toggle ( String )
* contains( String )

