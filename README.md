https://github.com/robots4life/multi-leaflet-svelte/blob/master/src/components/LeafletMap.svelte#L33

1.

Why does `map.remove()` here lead to this error below ?
If it is inside the condition `if (map)` it works ok.

2.

After `map.remove()` is called inside the condition, `map` can still be logged, why is that ?

3.

How can I make sure that after `map.remove()` and when navigating to `/page`, so when `onDestroy` is finished, the `map` is not left in memory or in the component ?

```js
onDestroy(() => {
	if (map) {
		console.log('Removing map..');
		console.log(map);
		map.remove();
		console.log(map);
	}
	// this breaks - why ?
	// map.remove();
});
```

Error when calling `map.remove();` outside the condition.

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
