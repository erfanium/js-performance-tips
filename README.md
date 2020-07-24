# JS / TS Performance tips

#### Use promise.catch instead of try/catch (36% faster!)
```js
// Don't use
try {
   await op()
} catch(e) {
   // some stuff
}

// Use
await op()
  .catch((e) => { 
    // some stuff
  })
```
