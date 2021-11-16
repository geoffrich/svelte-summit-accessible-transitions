<script>
	import { fly } from 'svelte/transition';
	export let transition = fly;
	export let params = { y: 30 };

	export let show = false;
</script>

<div>
	<div class="input">
		<input type="checkbox" id="show" bind:checked={show} /><label for="show"
			>Show box</label
		>
	</div>
	{#if show}
		<div class="box" transition:transition|local={params}>
			<span class="emoji"><slot>📦</slot></span>
		</div>
	{/if}
</div>

<style>
	.box {
		height: 100px;
		aspect-ratio: 1/1;
		background-color: cornflowerblue;
		margin: 1rem 0;
		display: grid;
		place-items: center;
	}

	input {
		height: 1em;
		width: 1em;
		margin-right: 0.5em;
	}

	.input {
		display: flex;
		align-items: center;
	}

	.emoji {
		font-size: 4rem;
	}
</style>
