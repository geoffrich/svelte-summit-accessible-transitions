<script>
	import WithTransition from '$lib/WithTransition.svelte';
	import { fly, fade, scale, slide, blur } from 'svelte/transition';

	let transition = fly;
	$: transitionName = options.find(([val, name]) => val === transition)[1];

	let options = [
		[fly, 'fly'],
		[fade, 'fade'],
		[scale, 'scale'],
		[slide, 'slide'],
		[blur, 'blur']
	];

	let duration;
</script>

<h1>Example 1</h1>
<div>
	<div class="container">
		<div>
			<label for="transition">Transition</label>
			<select bind:value={transition} id="transition">
				{#each options as [val, text]}
					<option value={val}>{text}</option>
				{/each}
			</select>
		</div>
		<WithTransition {transition} bind:duration />
	</div>
</div>

<style>
	select {
		max-width: 20ch;
		font-size: inherit;
		padding: 0.25em 0.5em;
		margin-bottom: 0.5rem;
	}

	.container {
		display: flex;
		flex-direction: column;
		gap: 0.5rem;
	}
</style>
