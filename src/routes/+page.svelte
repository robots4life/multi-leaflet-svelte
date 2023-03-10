<script>
	import LeafletMap from '$components/LeafletMap.svelte';

	const concerts = [
		{ latitude: 47.37515142664481, longitude: 8.534933254122734, zoom: 17 },
		{ latitude: 47.3847973, longitude: 8.5201642, zoom: 13 }
	];
</script>

<h1>Welcome to SvelteKit</h1>
<p>Visit <a href="https://kit.svelte.dev">kit.svelte.dev</a> to read the documentation</p>

{#each concerts as concert}
	<LeafletMap latitude={concert.latitude} longitude={concert.longitude} zoom={concert.zoom} />
{/each}
