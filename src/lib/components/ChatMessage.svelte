<script lang="ts">
	import { onDestroy } from 'svelte';

	export let role: 'user' | 'assistant';
	export let text: string;
	export let thinking: boolean = false;

	let displayText = text;
	let interval: NodeJS.Timeout | undefined;

	function start() {
		if (!interval) {
			const steps = ['.', '..', '...'];
			let idx = 0;
			displayText = steps[idx];
			interval = setInterval(() => {
				idx = (idx + 1) % steps.length;
				displayText = steps[idx];
			}, 500);
		}
	}

	function stop() {
		if (interval) {
			clearInterval(interval);
			interval = undefined;
		}
		displayText = text;
	}

	$: thinking ? start() : stop();

	onDestroy(() => stop());
</script>

<div class={`message ${role}`}>{displayText}</div>

<style>
	.message {
		padding: 0.5rem 1rem;
		margin: 0.25rem 0;
		border-radius: 1rem;
		/* box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1); */
	}
	.user {
		background-color: #d1e8ff;
		align-self: flex-end;
	}
	.assistant {
		background-color: #fff4d9;
		align-self: flex-start;
	}
</style>
