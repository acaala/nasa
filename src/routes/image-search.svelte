<script lang="ts">
	import UserImage from '$lib/UserImage.svelte';

	import Search from '$lib/Icons/Search.svelte';

	$: images = [];
	let userInput: string;

	const fetchUserSearch = async () => {
		const response = await fetch(`https://images-api.nasa.gov/search?q=
    ${userInput}`).then((r) => r.json());

		userInput = undefined;

		for (let key in response.collection.items) {
			if (images.length < 10) {
				images.push(response.collection.items[key]);
			}
		}
	};

	const handleKeyup = async (event) => {
		if (event.key === 'Enter' && userInput != undefined) {
			fetchUserSearch();
		}
	};
</script>

<svelte:window on:keyup={handleKeyup} />

<div>
	<h3>Search For an Image</h3>
	<div class="search">
		<input type="text" bind:value={userInput} />
		<button id="search-btn" on:click={fetchUserSearch}><Search /></button>
	</div>

	<div id="image-search-grid">
		{#if images.length > 0}
			{#each images as image}
				<UserImage {...image} />
			{/each}
		{/if}
	</div>
</div>

<style>
	#image-search-grid {
		display: grid;
		grid-template-columns: auto;
		grid-row-gap: 2rem;
	}
	h3 {
		text-align: center;
		color: var(--subtitle);
	}
	div {
		width: 80%;
		margin: 2.5rem auto;
	}

	.search {
		display: flex;
		justify-content: center;
	}

	input {
		width: 80%;
		background: none;
		border: none;
		border-bottom: 1px solid darkgray;
		color: var(--body);
		font-size: 16px;
		padding-left: 5px;
		outline: none;
		line-height: 1.625;
	}

	button {
		background: none;
		border: none;
		border-bottom: 1px solid darkgray;
		cursor: pointer;
		padding-top: 2px;
		padding-bottom: 2px;
	}
</style>
