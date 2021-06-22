<nav>
	<div>
		<p>&#128640</p>
		<a href="/"><h1>Nasa-Api</h1></a>
	</div>

	<ul>
		<li>
			<a href="/">Home</a>
		</li>
		<li>
			<a href="/space">Image Search</a>
		</li>
	</ul>
</nav>

<style>
	nav {
		display: flex;
		align-items: center;
		justify-content: space-around;
	}
	ul {
		display: flex;
		list-style: none;
		justify-content: space-around;
		width: 33%;
	}
	a {
		color: var(--body);
		border-bottom: none;
		text-decoration: none;
	}
	a:hover {
		color: white;
	}

	h1 {
		color: white;
	}

	div {
		display: flex;
		align-items: center;
		color: white;
		padding-left: 0.5rem;
		padding-right: 0.5rem;
	}

	p {
		margin-right: 0.5rem;
	}
</style>
