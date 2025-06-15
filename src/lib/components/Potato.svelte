<script lang="ts">
	import ChatWindow from './ChatWindow.svelte';
</script>

<div class="potato">
	<ChatWindow />
</div>

<style>
	.potato {
		display: flex;
		flex-direction: column;
		align-items: center;
		justify-content: center;
		min-height: 100vh;
		padding: 1rem;
	}

	.potato h1 {
		font-size: 2rem;
		margin-bottom: 1rem;
	}

	.potato p {
		font-size: 1.25rem;
		margin-bottom: 2rem;
	}
</style>
