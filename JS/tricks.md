# Parse URL

```js
function parseURL(url) {
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

