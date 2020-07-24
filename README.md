# JS / TS Performance tips

#### Don't use Object literals for basic object transforms (5X faster!)
```
// Bad
function f(o) {
   const { _id, _v, ...b } = o
   return {
      id: _id,
      v: _v,
      ...b
   } 
}

// Good
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
// Bad
try {
   await op()
} catch(e) {
   // some stuff
}

// Good
await op()
  .catch((e) => { 
    // some stuff
  })
```
