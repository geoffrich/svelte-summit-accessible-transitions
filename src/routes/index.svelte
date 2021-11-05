<script>
	const exampleModules = import.meta.glob('./examples/*.svelte');
	const examples = [];
	for (const path in exampleModules) {
		const route = path.replace('.', '').replace('.svelte', '');
		const filename = route.split('/')[2].substring(2);
		const name = filename.replace(/_/g, ' ');
		examples.push([route, name]);
	}
</script>

<h1>Svelte Transitions and Accessibility</h1>

<h2>Examples</h2>

<ul>
	{#each examples as [route, name]}
		<li><a href={route}>{name}</a></li>
	{/each}
</ul>

<style>
	ul {
		margin: 0;
		padding-left: 1.25rem;
	}
	li + li {
		margin-top: 0.5rem;
	}

	a {
		text-transform: capitalize;
	}
</style>
