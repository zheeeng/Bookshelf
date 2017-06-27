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

# Flatten array

```js
function flatten () {
  return [].concat.apply([], arguments)
}
```

# Get global object under non-strict model

```
var g = (function () {return this})()
```

# Check if environment support 'use strict'
<http://stackoverflow.com/questions/3277182/how-to-get-the-global-object-in-javascript>

```
function isStrictSupported () {
  return (function () { 'use strict'; return this })()
}
```

# Get object type

```js
function getType (obj) {
  return (({}).toString.call(obj).match(/\[object\ (\w+)\]/)[1]).toLowerCase()
}
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

# Get pseudo element style

```js
var style = window.getComputedStyle(element[, pseudoElt])
var property = window.getComputedStyle(element[, pseudoElt]).getPropertyValue(property)
```

# Add css rule into stylesheet

```js
function addCSSRule(sheet, selector, rules, index) {
  if(sheet.insertRule) {
    sheet.insertRule(selector + "{" + rules + "}", index)
  }
  else {
    sheet.addRule(selector, rules, index)
  }
}
```

## CSSStyleSheet.insertRule

**Syntax**

```js
stylesheet.insertRule(rule, index)
```

* rule is a DOMString containing the rule to be inserted
* index is an unsigned int representing the position to insert at, where index-0 is first rule, and index-max(styleSheet.cssRules.length) is just after last rule and same as length of rule-list in spreadsheet.
* Chrome: " [Warning-icon] Calling CSSStyleSheet.insertRule() with one argument is deprecated. Please pass the index argument as well"
* Internet Explorer - pre v9: `addRule(selector, rule [, index])`

# Post error log

```js
window.addEventListener('error', function (e) {
    var stack = e.error.stack
    var message = e.error.toString()
    if (stack) {
        message += '\n' + stack
    }
    var xhr = new XMLHttpRequest()
    xhr.open('POST', '/log', true)
    xhr.send(message)
})
```

# Constantize object

```js
function constantize (obj) {
  Object.freeze(obj);
  Object.keys(obj).forEach(function (key, value) {
    if (typeof obj[key] === 'object') {
      constantize(obj[key])
    }
  })
}
```

# Check DOM Object
<http://stackoverflow.com/questions/384286/javascript-isdom-how-do-you-check-if-a-javascript-object-is-a-dom-object>

```js
//Returns true if it is a DOM node
function isNode(o){
  return (
    typeof Node === "object" ? o instanceof Node : 
    o && typeof o === "object" && typeof o.nodeType === "number" && typeof o.nodeName==="string"
  );
}

//Returns true if it is a DOM element    
function isElement(o){
  return (
    typeof HTMLElement === "object" ? o instanceof HTMLElement : //DOM2
    o && typeof o === "object" && o !== null && o.nodeType === 1 && typeof o.nodeName==="string"
);
}
```

# Class Multiple extend

```
function mix(...mixins) {
  return mixins.reduce((Mix, mixin) => {
    copyProperties(Mix, mixin)
    copyProperties(Mix.prototype, mixin.prototype)
    return Mix
  }, class {})
}
function copyProperties(target, source) {
  for (let key of Reflect.ownKeys(source)) {
    if (key !== "constructor" && key !== "prototype" && key !== "name") {
      let desc = Object.getOwnPropertyDescriptor(source, key)
      Object.defineProperty(target, key, desc)
    }
  }
}
```

