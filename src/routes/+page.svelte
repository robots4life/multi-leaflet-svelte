<script>
	import LeafletMap from '$components/LeafletMap.svelte';
	// import LeafletMarker from '$components/LeafletMarker.svelte';

	const concerts = [
		{
			latitude: 45.8150108,
			longitude: 15.981919,
			zoom: 12,
			locationLabel: 'Zagreb'
		},
		{ latitude: 40.7127837, longitude: -74.0059413, zoom: 10, locationLabel: 'New York' }
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

	<!-- {#each concerts as concert}
		<LeafletMap latitude={concert.latitude} longitude={concert.longitude} zoom={concert.zoom}>
			<LeafletMarker
				latitude={concert.latitude}
				longitude={concert.longitude}
				locationLabel={concert.locationLabel}
			/></LeafletMap
		>
		<hr />
	{/each} -->
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
