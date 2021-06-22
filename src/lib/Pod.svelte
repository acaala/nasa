<script>
	export let url;
	export let title;
	export let explanation;
	export let date;

	let show = false;
	$: rotate = show;
</script>

<main>
	<div class="image-div">
		<img src={url} alt={title} />
	</div>
	<div class="title-line">
		<h2>{title}</h2>
		<h3>{date}</h3>
	</div>
	<p class:show>{explanation}</p>

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
</main>

<style>
	.show {
		display: inline-block;
	}

	.rotate {
		transform: rotate(180deg);
	}

	.title-line {
		display: flex;
		align-items: center;
		justify-content: space-between;
		width: 95%;
	}

	h2 {
		color: white;
	}

	h3 {
		color: var(--subtitle);
	}

	p {
		line-height: 1.625;
		color: var(--body);
		display: none;
		width: 95%;
		font-size: 16px;
	}
	main {
		display: flex;
		margin: auto;
		flex-direction: column;
		align-items: center;
		width: 80%;
		height: 50%;
		border-radius: 50px;
		background: #202023;
		box-shadow: 6px 6px 12px #0d0d0e, -6px -6px 12px #333338;
	}
	.image-div {
		height: 500px;
		margin: 0.1rem;
	}
	img {
		width: 100%;
		height: 100%;
		border-radius: 50px 50px 5px 5px;
		object-fit: fill;
		object-position: center;
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

	@media screen and (max-width: 1000px) {
		h2 {
			font-size: 20px;
			padding-top: 0.2rem;
		}
		h3 {
			margin-bottom: -1rem;
			font-size: 16px;
		}

		.title-line {
			display: flex;
			flex-direction: column-reverse;
		}
	}

	@media screen and (min-width: 1100px) {
		main {
			max-width: 850px;
		}
	}
	@media screen and (max-width: 540px) {
		h2 {
			font-size: 16px;
		}
		h3 {
			font-size: 14px;
		}
		p {
			font-size: 14px;
		}
	}
</style>
