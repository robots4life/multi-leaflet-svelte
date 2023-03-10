<script>
	import { getContext } from 'svelte';
	import { leaflet, key } from '$lib/leaflet.js';

	const { getMap } = getContext(key);
	const map = getMap();

	export let latitude;
	export let longitude;
	// export let zoom;

	leaflet
		.marker([latitude, longitude])
		.addTo(map)
		.bindPopup('A pretty CSS3 popup.<br> Easily customizable.')
		.openPopup();

	// const popup = new mapbox.Popup({ offset: 25 }).setText(label);

	// const marker = new mapbox.Marker().setLngLat([lon, lat]).setPopup(popup).addTo(map);
</script>
