<script lang="ts">
	// import nav
	import Nav from '$lib/components/Nav.svelte';
	import favicon from '$lib/assets/favicon.svg';

	let { children } = $props();

	

</script>

<svelte:head>
	<link rel="icon" href={favicon} />
	<title>Hello App</title>
</svelte:head>
<!-- nav -->
<Nav />
{@render children()}
