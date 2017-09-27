# Snippets

## Promisify

```ts
type NodeStyleCallback<Ret> = (err: any, data: Ret) => void
type NodeStyleCallbackCallingFunction<Data, Ret> = (data: Data, cb: NodeStyleCallback<Ret>) => void
interface Promisify {
  <Data, Ret>(func: NodeStyleCallbackCallingFunction<Data, Ret>): (data: Data) => Promise<Ret>
}

const promisify: Promisify = func => data => new Promise((resolve, reject) => {
  func(data, (err, data) => {
    err ? reject(err) : resolve(data)
  })
})
```

## strEnum
[https://basarat.gitbooks.io/typescript/content/docs/types/literal-types.html#string-based-enums]

```ts
function strEnum<T extends string>(o: Array<T>): {[K in T]: K} {
  return o.reduce((res, key) => {
    res[key] = key;
    return res;
  }, Object.create(null));
}

/**
  * Sample create a string enum
  *
  **/

/** Create a K:V */
const Direction = strEnum([
  'North',
  'South',
  'East',
  'West'
])
/** Create a Type */
type Direction = keyof typeof Direction;

/**
  * Sample using a string enum
  */
let sample: Direction;

sample = Direction.North; // Okay
sample = 'North'; // Okay
sample = 'AnythingElse';
```
