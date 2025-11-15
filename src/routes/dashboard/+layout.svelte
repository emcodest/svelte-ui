<script lang="ts">
	// import nav
	import NavDash from '$lib/components/NavDash.svelte';
	import favicon from '$lib/assets/favicon.svg';

	let { children } = $props();

</script>

<svelte:head>
	<link rel="icon" href={favicon} />
	<title>Dashboard App</title>
</svelte:head>
<!-- nav -->
<NavDash />
{@render children()}