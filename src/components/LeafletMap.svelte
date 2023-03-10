<script>
	// https://svelte.dev/tutorial/context-api
	import { onDestroy, setContext } from 'svelte';
	import { leaflet, key } from '$lib/leaflet.js';

	setContext(key, {
		getMap: () => map
	});

	export let latitude;
	export let longitude;
	export let zoom;

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
		leaflet
			.marker([latitude, longitude])
			.addTo(map)
			.bindPopup('A pretty CSS3 popup.<br> Easily customizable.')
			.openPopup();
	}

	onDestroy(() => {
		if (map) map.remove();
	});
</script>

<div class="leaflet-map-container" bind:this={container}>
	{#if map}
		<slot />
	{/if}
</div>

<style>
	@import 'leaflet/dist/leaflet.css';
	.leaflet-map-container {
		height: 800px;
	}
</style>
