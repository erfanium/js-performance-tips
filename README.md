# JS / TS Performance tips

#### Don't use Object literals for basic object transforms (5X faster!)
```js
// Slow
function f(o) {
   const { _id, _v, ...b } = o
   return {
      id: _id,
      v: _v,
      ...b
   } 
}

// Fast
function f(o) {Object literals
   return {
      id: o._id,
      v: o._v,
      a: o.a,
      b: o.b,
   } 
}

f({ _id: 1, _v: 1, a: "foo", b: "bar" })
```

#### Use promise.catch instead of try/catch (36% faster!)
```js
// Slow
try {
   await op()
} catch(e) {
   // some stuff
}

// Fast
await op()
  .catch((e) => { 
    // some stuff
  })
```

#### Use abstract functions instead of `function.bind` (37% faster!) 
I personally thought function binding would be faster!

```js
// Slow
const a = f.bind(this, "a")
a(1)

// Fast
const a = (n) => f("a", n)
a(1)
```
