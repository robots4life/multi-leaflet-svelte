<script>
	import { onMount, onDestroy, tick } from 'svelte';
	import { leaflet } from '$lib/leaflet.js';
	export let latitude;
	export let longitude;
	export let zoom;
	export let locationLabel;

	let container;
	let map;

	onMount(async () => {
		map = new leaflet.map(container).setView([latitude, longitude], zoom);

		leaflet
			.tileLayer('https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png', {
				attribution:
					'&copy; <a href="https://www.openstreetmap.org/copyright">OpenStreetMap</a> contributors'
			})
			.addTo(map);

		leaflet.marker([latitude, longitude]).addTo(map).bindPopup(locationLabel).openPopup();
	});

	// https://discord.com/channels/525725325007650828/1081935571015958528/1084506148192931921
	onDestroy(async () => {
		map.remove();
		map = null;
		console.log(map);
	});
</script>

<div class="leaflet-map-container" bind:this={container} />

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
