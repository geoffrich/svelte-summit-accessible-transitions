<script>
	import WithTransition from '$lib/WithTransition.svelte';
</script>

<h1>Disable all animation</h1>
<div class="container two-col">
	<pre>{`
@media (prefers-reduced-motion: reduce) {
	* {
		animation-duration: 0.01ms !important;
		animation-iteration-count: 1 !important;
		transition-duration: 0.01ms !important;
		animation-delay: 0.01ms !important;
	}
}`}</pre>
	<WithTransition>🐰</WithTransition>
</div>

<style>
	@media (prefers-reduced-motion: reduce) {
		.container :global(*) {
			animation-duration: 0.01ms !important;
			animation-iteration-count: 1 !important;
			transition-duration: 0.01ms !important;
			animation-delay: 0.01ms !important;
		}
	}
</style>
