<script lang="ts">
	import { Loader, type LoaderOptions } from '@googlemaps/js-api-loader';

	import { onMount } from 'svelte';
	export let apiKey: string;
	export let loaderOptions: Omit<LoaderOptions, 'apiKey'> | null = null;
	export let mapOptions: google.maps.MapOptions | null = null;

	let map: google.maps.Map;

	let container: HTMLElement;

	onMount(() => {
		const loader = new Loader({
			version: 'quarterly',
			...loaderOptions,
			apiKey
		});

		loader.load().then(() => {
			map = new google.maps.Map(container, {
				center: { lat: -34.397, lng: 150.644 },
				zoom: 3,
				minZoom: 3,
				gestureHandling: 'greedy',
				streetViewControl: false,
				...mapOptions
			});
		});
	});
</script>

<div bind:this={container} id="map" {...$$restProps} />

<style>
	#map {
		min-height: 100vh;
	}
</style>
