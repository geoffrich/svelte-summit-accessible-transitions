<script>
	import WithTransition from '$lib/WithTransition.svelte';
	import { fly, fade } from 'svelte/transition';
	import { browser } from '$app/env';
	import { onDestroy } from 'svelte';

	let transitionToUse = fade;

	if (browser) {
		const query = window.matchMedia('(prefers-reduced-motion: reduce)');
		const handleChange = (event) => {
			transitionToUse = getTransition(event.matches);
		};

		transitionToUse = getTransition(query.matches);

		query.addEventListener('change', handleChange);

		onDestroy(() => {
			query.removeEventListener('change', handleChange);
		});
	}

	function getTransition(isReducedMotion) {
		return isReducedMotion ? fade : fly;
	}
</script>

<h1>With Match Media</h1>
<div class="container two-col">
	<pre>{`
const query = window.matchMedia('(prefers-reduced-motion: reduce)');
let transitionToUse = getTransition(query.matches);

query.addEventListener('change', (event) => {
	transitionToUse = getTransition(event.matches);
});

function getTransition(isReducedMotion) {
	return isReducedMotion ? fade : fly;
}
	`}</pre>
	<WithTransition transition={transitionToUse}>🐱</WithTransition>
</div>
