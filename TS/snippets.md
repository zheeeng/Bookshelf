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
