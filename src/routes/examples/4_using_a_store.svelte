<script>
	import WithTransition from '$lib/WithTransition.svelte';
	import { fly, fade } from 'svelte/transition';
	import reducedMotion from '$lib/reducedMotionStore';

	$: transitionToUse = $reducedMotion ? fade : fly;
</script>

<h1>With a Store</h1>
<div class="container two-col">
	<WithTransition transition={transitionToUse}>🐶</WithTransition>
</div>
