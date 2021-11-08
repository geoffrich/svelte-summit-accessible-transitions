<script>
	import WithTransition from '$lib/WithTransition.svelte';
	import { fly, fade } from 'svelte/transition';
	import { writable } from 'svelte/store';
	import { browser } from '$app/env';

	const initial = browser ? window.matchMedia('(prefers-reduced-motion: reduce)').matches : false;
	const reducedMotion = writable(initial);

	$: transitionToUse = $reducedMotion ? fade : fly;

	function handleToggle() {
		$reducedMotion = !$reducedMotion;
	}
</script>

<h1>Custom Toggle</h1>
<button on:click={handleToggle}>Toggle ({$reducedMotion})</button>
<div class="container two-col">
	<WithTransition transition={transitionToUse}>🐶</WithTransition>
</div>
