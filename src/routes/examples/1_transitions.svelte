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
<div class="two-col">
	<pre>{`
<input type="checkbox" id="show" bind:checked={show} />
<label for="show">Show box</label>
{#if show}
    <div class="box" transition:${transitionName} />
{/if}
    `}</pre>
	<div class="container">
		<div>
			<label for="transition">Transition</label>
			<select bind:value={transition} id="transition">
				{#each options as [val, text]}
					<option value={val}>{text}</option>
				{/each}
			</select>
		</div>
		<div>
			<label for="duration">Duration</label>
			<input id="duration" type="number" bind:value={duration} />
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

	input {
		max-width: 10ch;
	}
</style>
