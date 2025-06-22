<script lang="ts">
	import { onDestroy } from 'svelte';

	export let open: boolean = false;

	function start() {
		console.log('Starting...');
	}

	function stop() {
		console.log('Stopping...');
	}

	$: open ? start() : stop();
	$: state = open ? 'visible' : 'hidden';

	onDestroy(() => stop());
</script>

<div class={`floating ${state}`}>lmaoooooo</div>

<style>
	.floating {
		display: flex;
		font-size: xx-large;
		padding: 0.5rem 1rem;
		margin: 0.25rem 0;
		border-radius: 1rem;
		/* box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1); */
	}
	.hidden {
		visibility: hidden;
	}
	.visible {
		visibility: visible;
	}
</style>
