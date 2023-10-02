<script>
	import '../app.postcss';
</script>

<nav class="bg-red-900 text-white p-3 mb-5">
	<div class="container mx-auto flex justify-center">
		<h1 class="font-extrabold text-3xl slanted-text">NewsAgg</h1>
	</div>
</nav>

<slot />

<style lang="postcss">
	:global(html) {
		background-color: rgb(49, 49, 49);
		color: theme(colors.white);
	}
	.slanted-text {
		transform: skew(-10deg); /* Adjust the angle as needed */
		display: inline-block; /* Maintain the block layout */
	}
</style>
