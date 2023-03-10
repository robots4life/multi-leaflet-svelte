<script>
	import LeafletMap from '$components/LeafletMap.svelte';
	// import LeafletMarker from '$components/LeafletMarker.svelte';

	const concerts = [
		{
			latitude: 47.37515142664481,
			longitude: 8.534933254122734,
			zoom: 17,
			locationLabel: 'Stall 6'
		},
		{ latitude: 47.3847973, longitude: 8.5201642, zoom: 10, locationLabel: 'Hive Club' }
	];
</script>

<div id="wrap">
	<h1>Welcome to SvelteKit</h1>
	<p>Visit <a href="https://kit.svelte.dev">kit.svelte.dev</a> to read the documentation</p>

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
	#wrap,
	h1,
	p {
		text-align: center;
	}
</style>
