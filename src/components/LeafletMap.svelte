<script>
	import { onMount, onDestroy } from 'svelte';
	import { leaflet } from '$lib/leaflet.js';
	export let latitude;
	export let longitude;
	export let zoom;
	export let locationLabel;

	let container;
	let map;

	onMount(() => {
		map = new leaflet.map(container).setView([latitude, longitude], zoom);

		leaflet
			.tileLayer('https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png', {
				attribution:
					'&copy; <a href="https://www.openstreetmap.org/copyright">OpenStreetMap</a> contributors'
			})
			.addTo(map);

		leaflet.marker([latitude, longitude]).addTo(map).bindPopup(locationLabel).openPopup();
	});

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
</script>

<div class="leaflet-map-container" bind:this={container}>
	{#if map}
		{console.log(map)}
	{/if}
</div>

<style>
	@import 'leaflet/dist/leaflet.css';
	.leaflet-map-container {
		border: 4px solid green;
		height: 300px;
		width: 800px;
		margin-left: auto;
		margin-right: auto;
	}
</style>
