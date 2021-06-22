<script>
	export let data;
	export let links;

	let show = false;
	$: rotate = show;
</script>

<main>
	{#if links != undefined}
		<div>
			<img src={links[0].href} alt={data[0].nasa_id} />
		</div>
	{/if}

	<h4>{data[0].location}</h4>
	<p class:show>{data[0].description}</p>

	<div>
		<button
			on:click={() => {
				(show = !show), (rotate = !rotate);
			}}
			>Show {show ? 'Less' : 'More'}
			<svg
				fill="none"
				stroke="currentColor"
				stroke-linecap="round"
				stroke-linejoin="round"
				stroke-width="2"
				viewBox="0 0 24 24"
				class:rotate
			>
				<path d="M6 9l6 6 6-6" />
			</svg>
		</button>
	</div>
</main>

<style>
	main {
		border-radius: 25px;
		background: #202023;
		box-shadow: 6px 6px 12px #0d0d0e, -6px -6px 12px #333338;
		width: 80%;
		max-width: 600px;
	}
	h4 {
		color: var(--subtitle);
		font-size: 18px;
		padding-left: 0.5rem;
	}
	p {
		line-height: 1.625;
		color: var(--body);
		display: none;
		width: 95%;
		font-size: 16px;
		margin: auto;
	}

	img {
		width: 100%;
		border-radius: 25px;
	}

	.show {
		display: inline-block;
	}

	.rotate {
		transform: rotate(180deg);
	}

	div {
		display: flex;
		justify-content: center;
	}

	button {
		cursor: pointer;
		background: none;
		border: none;
		color: var(--cta);
		font-size: 16px;
		margin-top: 0.5rem;
		margin-bottom: 0.5rem;
	}

	svg {
		height: 16px;
	}
</style>
