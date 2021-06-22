<script>
	import Nav from '$lib/Nav.svelte';
</script>

<svelte:head>
	<style>
		body {
			background: rgb(32, 32, 35);
			font-family: 'Poppins';
		}
	</style>
	<link href="https://fonts.googleapis.com/css?family=Poppins" rel="stylesheet" />
</svelte:head>

<Nav />
<slot />

<style>
	:root {
		--subtitle: rgb(107, 114, 128);
		--body: rgb(156, 163, 175);
		--cta: rgb(129, 140, 248);
	}
</style>
