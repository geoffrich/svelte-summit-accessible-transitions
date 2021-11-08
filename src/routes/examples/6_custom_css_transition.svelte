<script>
	import { fade } from 'svelte/transition';
	import { elasticOut } from 'svelte/easing';
	import reducedMotion from '$lib/reducedMotionStore';

	let visible = false;

	// from https://svelte.dev/tutorial/custom-css-transitions
	function spin(node, { duration }) {
		return {
			duration,
			css: (t) => {
				const eased = elasticOut(t);

				return `
					transform: scale(${$reducedMotion ? 1 : eased}) rotate(${$reducedMotion ? 0 : eased * 1080}deg);
                    opacity: ${$reducedMotion ? t : 1};
					color: hsl(
						${Math.trunc(t * 360)},
						${Math.min(100, 1000 - 1000 * t)}%,
						${Math.min(50, 500 - 500 * t)}%
					);`;
			}
		};
	}
</script>

<h1>Custom CSS Transition</h1>

<label>
	<input type="checkbox" bind:checked={visible} />
	visible
</label>

{#if visible}
	<div class="centered" in:spin={{ duration: $reducedMotion ? 1000 : 8000 }} out:fade>
		<span>transitions!</span>
	</div>
{/if}

<style>
	.centered {
		position: absolute;
		left: 50%;
		top: 50%;
		transform: translate(-50%, -50%);
	}

	span {
		position: absolute;
		transform: translate(-50%, -50%);
		font-size: 4em;
	}
</style>
