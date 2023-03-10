<script>
	// https://svelte.dev/tutorial/context-api
	// import { onMount, onDestroy, setContext } from 'svelte';
	import { onDestroy, onMount } from 'svelte';

	// import { leaflet, key } from '$lib/leaflet.js';
	import { leaflet } from '$lib/leaflet.js';

	// setContext(key, {
	// 	getMap: () => map
	// });

	export let latitude;
	export let longitude;
	export let zoom;
	export let locationLabel;

	let container;
	let map;

	function load() {
		map = new leaflet.map(container).setView([latitude, longitude], zoom);

		leaflet
			.tileLayer('https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png', {
				attribution:
					'&copy; <a href="https://www.openstreetmap.org/copyright">OpenStreetMap</a> contributors'
			})
			.addTo(map);

		leaflet.marker([latitude, longitude]).addTo(map).bindPopup(locationLabel).openPopup();
	}

	onMount(() => {
		load();
	});

	onDestroy(() => {
		if (map) map.remove();
	});
</script>

<div class="leaflet-map-container" bind:this={container}>
	<!-- {#if map}
		<slot />
	{/if} -->
</div>

<style>
	@import 'leaflet/dist/leaflet.css';
	.leaflet-map-container {
		border: 4px solid green;
		height: 800px;
		width: 800px;
		margin-left: auto;
		margin-right: auto;
	}
</style>
