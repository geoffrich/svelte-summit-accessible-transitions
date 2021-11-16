<script>
	import WithTransition from '$lib/WithTransition.svelte';
</script>

<h1>Disable all animation</h1>
<div class="container">
	<WithTransition>🐰</WithTransition>
</div>

<style>
	@media (prefers-reduced-motion: reduce) {
		/* Scoped to this container so that I can use other methods in other examples */
		.container :global(*) {
			animation-duration: 0.01ms !important;
			animation-iteration-count: 1 !important;
			transition-duration: 0.01ms !important;
			animation-delay: 0.01ms !important;
		}
	}
</style>
