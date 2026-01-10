<script lang="ts">
	import { page } from '$app/state'; // Svelte 5 way to access page state
	import { onMount } from 'svelte';
	import { browser } from '$app/environment';

	const DOMAIN = '3xw.ca';

	// Replace with your actual GoatCounter URL
	const GOATCOUNTER_URL = `https://stats.${DOMAIN}/count`;

	onMount(() => {
		if (!browser) return;

		// 1. Load the script manually
		const script = document.createElement('script');
		script.async = true;
		script.src = `//stats.${DOMAIN}/count.js`;
		script.dataset.goatcounter = GOATCOUNTER_URL;
		document.head.appendChild(script);
	});

	// 2. Track page views on route change
	// We use a $derived or $effect to react to path changes
	$effect(() => {
		const path = page.url.pathname;

		// Check if the goatcounter object exists on the window
		if (window.goatcounter && window.goatcounter.count) {
			window.goatcounter.count({
				path: path
			});
		}
	});
</script>
