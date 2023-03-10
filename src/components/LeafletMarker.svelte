<script>
	import { getContext } from 'svelte';
	import { leaflet, key } from '$lib/leaflet.js';

	const { getMap } = getContext(key);
	const map = getMap();

	export let latitude;
	export let longitude;

	leaflet
		.marker([latitude, longitude])
		.addTo(map)
		.bindPopup('A pretty CSS3 popup.<br> Easily customizable.')
		.openPopup();
</script>
