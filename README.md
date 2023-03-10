1.  https://github.com/robots4life/multi-leaflet-svelte/blob/master/src/components/LeafletMap.svelte#L45

Why does `map.remove()` here lead to this error ? If it is inside the condition it works ok.

```js
Map.js:747 Uncaught (in promise) Error: Map container is being reused by another instance
    at NewClass.remove (Map.js:747:10)
    at LeafletMap.svelte:45:7
    at run (index.mjs:20:12)
    at Array.forEach (<anonymous>)
    at run_all (index.mjs:26:9)
    at destroy_component (index.mjs:2056:9)
    at Object.destroy [as d] (+page.svelte:27:8)
    at destroy_each (index.mjs:383:27)
    at Object.destroy [as d] (+page.svelte:20:8)
    at destroy_component (index.mjs:2057:36)
```

2.  https://github.com/robots4life/multi-leaflet-svelte/blob/master/src/components/LeafletMap.svelte#L52

What is `<slot />` here used for ?
