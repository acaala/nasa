<script lang="ts">
	import { API_KEY } from '$lib/Env.js';
	import ImageSearch from '$lib/ImageSearch.svelte';
	import Pod from '$lib/Pod.svelte';
	import { onMount } from 'svelte';
	import type { IData } from 'types';
	import Layout from './__layout.svelte';

	let pod = {} as IData;

	async function fetchPod() {
		pod = await fetch(`https://api.nasa.gov/planetary/apod?api_key=${API_KEY}`).then((r) =>
			r.json()
		);
	}

	onMount(fetchPod);
</script>

<h3>Picture of the day</h3>
<Pod {...pod} />
<ImageSearch />

<style>
	h3 {
		text-align: center;
		color: var(--subtitle);
	}
</style>
