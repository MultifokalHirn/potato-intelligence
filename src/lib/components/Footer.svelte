<script lang="ts">
	const year = new Date().getFullYear();
</script>

<footer>
	&copy;{year} &mdash; made with ❤️ by
	<a
		href="https://github.com/MultifokalHirn"
		target="_blank"
		rel="noopener noreferrer"
		style="color: #4078c0; text-decoration: none;"
	>
		MultifokalHirn
	</a>
</footer>

<style>
	footer {
		position: fixed;
		bottom: 0;
		left: 0;
		width: 100%;
		background: #fff;
		text-align: right;
		/* border-top: 1px dotted black; */
		/* color: #fff; */
		padding: 1rem;
		font-size: 0.95rem;
		/* box-shadow: 0 2px 8px rgba(0, 0, 0, 0.1); */
		z-index: 1000;
	}
</style>
