<script lang="ts">
	import FloatingPopup from '$lib/components/FloatingPopup.svelte';
	import Potato from '$lib/components/Potato.svelte';

	let showPopup = false;
</script>

<div class="container">
	<div
		role="button"
		tabindex="0"
		on:mouseover={() => {
			showPopup = true;
		}}
		on:mouseout={() => {
			showPopup = false;
		}}
		on:focus={() => {
			showPopup = true;
		}}
		on:blur={() => {
			showPopup = false;
		}}
	>
		ertz
	</div>
	<FloatingPopup open={showPopup} />
	<Potato />
</div>

<style>
	.container {
		display: flex;
		flex-direction: column;
		align-items: center;
		justify-content: center;
		min-height: 50vh;
		/* background-color: #f0f0f0; */
	}
</style>
