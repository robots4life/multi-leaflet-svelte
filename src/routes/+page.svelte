<script>
	import LeafletMap from '$components/LeafletMap.svelte';

	const concerts = [
		{
			latitude: 45.8150108,
			longitude: 15.981919,
			zoom: 12,
			locationLabel: 'Zagreb'
		},
		{ latitude: 40.7127837, longitude: -74.0059413, zoom: 10, locationLabel: 'New York' },
		{ latitude: 48.856614, longitude: 2.3522219, zoom: 15, locationLabel: 'Paris' },
		{ latitude: 35.7090259, longitude: 139.73199249999993, zoom: 15, locationLabel: 'Tokyo' }
	];
</script>

<div class="wrap">
	<a href="/page">Page</a>
	<h1>Welcome to SvelteKit</h1>

	{#each concerts as concert}
		<LeafletMap
			latitude={concert.latitude}
			longitude={concert.longitude}
			zoom={concert.zoom}
			locationLabel={concert.locationLabel}
		/>
		<hr />
	{/each}
</div>

<style>
	.wrap,
	h1 {
		text-align: center;
	}
	a {
		font-size: 2rem;
	}
</style>
