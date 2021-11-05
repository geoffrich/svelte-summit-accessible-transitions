<script>
	import '../app.css';

	import reducedMotionStore from '$lib/reducedMotionStore';
</script>

<svelte:head>
	<title>Svelte Transitions and Accessibility</title>
</svelte:head>

<header>
	<nav>
		<a href="/">Examples</a>
	</nav>
	<div>Reduced motion: {$reducedMotionStore}</div>
</header>

<main>
	<slot />
</main>

<style>
	main {
		flex: 1;
		display: flex;
		flex-direction: column;
	}

	header {
		display: flex;
		gap: 1rem;
		padding: 1rem;
	}

	main,
	header {
		padding: 1rem;
		width: 100%;
		max-width: 1024px;
		margin: 0 auto;
	}
</style>
