<script lang="ts">
	import '../app.css';
	import favicon from '$lib/assets/favicon.svg';
	import Analytics from '$lib/analytics.svelte';

	let { children } = $props();
</script>

<svelte:head>
	<link rel="icon" href={favicon} />
</svelte:head>

{@render children?.()}

<Analytics />
