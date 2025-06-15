<script lang="ts">
	export let role: 'user' | 'assistant';
	export let text: string;
</script>

<div class={`message ${role}`}>{text}</div>

<style>
	.message {
		padding: 0.25rem 0.5rem;
		margin: 0.25rem 0;
		border-radius: 0.375rem;
	}
	.user {
		background-color: #e5f2ff;
		align-self: flex-end;
	}
	.assistant {
		background-color: #f4f4f4;
		align-self: flex-start;
	}
</style>
