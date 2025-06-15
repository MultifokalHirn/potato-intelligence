<script lang="ts">
	import ChatMessage from './ChatMessage.svelte';

	interface Message {
		role: 'user' | 'assistant';
		text: string;
		thinking?: boolean;
	}

	let messages: Message[] = [];
	let input = '';

	function send() {
		const text = input.trim();
		if (!text) return;
		messages = [...messages, { role: 'user', text }];
		input = '';

		const thinkingMessage: Message = { role: 'assistant', text: '', thinking: true };
		messages = [...messages, thinkingMessage];

		setTimeout(() => {
			thinkingMessage.thinking = false;
			thinkingMessage.text = '🥔';
			messages = [...messages];
		}, 2000);
	}

	function handleKey(event: KeyboardEvent) {
		if (event.key === 'Enter' && !event.shiftKey) {
			event.preventDefault();
			send();
		}
	}
</script>

<div class="chat-window">
	{#if messages.length > 0}
		<div class="messages">
			{#each messages as m (m)}
				<ChatMessage role={m.role} text={m.text} thinking={m.thinking} />
			{/each}
		</div>
	{/if}
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
		max-width: 60rem;
		/* height: 100%; */
	}
	.messages {
		display: flex;
		flex-direction: column;
		gap: 0.25rem;
		border: 2px dashed #ddd;
		padding: 1rem;
		flex: 1;
		overflow-y: auto;
		/* background-color: #faf9f6; */
	}
	.input-row {
		display: flex;
		gap: 0.5rem;
	}
	textarea {
		flex: 1;
		padding: 0.5rem;
		border-radius: 0.5rem;
	}
	button {
		padding: 0.5rem 1rem;
		border-radius: 0.5rem;
		background-color: #ffd1dc;
		border: none;
		cursor: pointer;
	}
</style>
