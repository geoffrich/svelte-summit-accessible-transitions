<script>
	import WithTransition from '$lib/WithTransition.svelte';
	import { fly, fade } from 'svelte/transition';
	import { onDestroy } from 'svelte';
	import { browser } from '$app/env';

	let reducedMotion = false;
	$: transitionToUse = reducedMotion ? fade : fly;

	const reducedMotionQuery = '(prefers-reduced-motion: reduce)';

	if (browser) {
		let mediaQuery = window.matchMedia(reducedMotionQuery);
		reducedMotion = mediaQuery.matches;

		const setReducedMotion = (event) => {
			reducedMotion = event.matches;
		};

		mediaQuery.addEventListener('change', setReducedMotion);

		onDestroy(() => {
			mediaQuery.removeEventListener('change', setReducedMotion);
		});
	}
</script>

<h1>With Match Media</h1>
<div class="container two-col">
	<WithTransition transition={transitionToUse}>🐱</WithTransition>
</div>
