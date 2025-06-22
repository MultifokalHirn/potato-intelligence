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
		min-height: 40vh;
		min-width: 80vh;
		padding: 1rem;
	}
</style>
