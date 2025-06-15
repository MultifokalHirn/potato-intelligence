<script lang="ts">
	import ChatMessage from './ChatMessage.svelte';

	interface Message {
		role: 'user' | 'assistant';
		text: string;
	}

	let messages: Message[] = [];
	let input = '';

	function send() {
		const text = input.trim();
		if (!text) return;
		messages = [...messages, { role: 'user', text }];
		input = '';
		// respond with potato emoji
		messages = [...messages, { role: 'assistant', text: '🥔' }];
	}

	function handleKey(event: KeyboardEvent) {
		if (event.key === 'Enter' && !event.shiftKey) {
			event.preventDefault();
			send();
		}
	}
</script>

<div class="chat-window">
	<div class="messages">
		{#each messages as m (m)}
			<ChatMessage role={m.role} text={m.text} />
		{/each}
	</div>
	<div class="input-row">
		<textarea bind:value={input} on:keydown={handleKey} rows="2" placeholder="Ask me anything..."
		></textarea>
		<button on:click={send}>Ask</button>
	</div>
</div>

<style>
	.chat-window {
		display: flex;
		flex-direction: column;
		gap: 0.5rem;
		width: 100%;
		max-width: 30rem;
	}
	.messages {
		display: flex;
		flex-direction: column;
		gap: 0.25rem;
		border: 1px solid #ddd;
		padding: 0.5rem;
		min-height: 10rem;
		max-height: 20rem;
		overflow-y: auto;
	}
	.input-row {
		display: flex;
		gap: 0.5rem;
	}
	textarea {
		flex: 1;
		padding: 0.25rem;
	}
	button {
		padding: 0.25rem 0.75rem;
	}
</style>
