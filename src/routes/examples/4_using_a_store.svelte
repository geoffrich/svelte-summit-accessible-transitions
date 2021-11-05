<script>
	import WithTransition from '$lib/WithTransition.svelte';
	import { fly, fade } from 'svelte/transition';
	import { readable } from 'svelte/store';
	import { browser } from '$app/env';

	const reducedMotion = readable(false, (set) => {
		if (browser) {
			const query = window.matchMedia('(prefers-reduced-motion: reduce)');
			const setReducedMotion = (event) => {
				set(event.matches);
			};

			set(query.matches);
			query.addEventListener('change', setReducedMotion);

			return () => {
				query.removeEventListener('change', setReducedMotion);
			};
		}
	});

	$: transitionToUse = $reducedMotion ? fade : fly;
</script>

<h1>With a Store</h1>
<div class="container two-col">
	<pre>{`
const reducedMotion = readable(false, (set) => {
	const query = window.matchMedia('(prefers-reduced-motion: reduce)');
	const setReducedMotion = (event) => {
		set(event.matches);
	};

	set(query.matches);
	query.addEventListener('change', setReducedMotion);

	return () => {
		query.removeEventListener('change', setReducedMotion);
	};
});`}</pre>
	<WithTransition transition={transitionToUse}>🐶</WithTransition>
</div>
