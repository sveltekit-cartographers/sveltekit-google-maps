<script>
	import { env } from '$env/dynamic/public';
	import Map from '$lib/components/Map.svelte';
</script>

<Map apiKey={env.PUBLIC_GOOGLE_MAPS_API_KEY} />
