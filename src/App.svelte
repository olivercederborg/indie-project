<script>
	import SearchBar from './lib/SearchBar.svelte'
</script>

<main>
	<section
		class="Search-section relative min-h-screen flex flex-col justify-center items-center bg-white"
	>
		<SearchBar />
	</section>
</main>

<style>
	.Search-section::after {
		content: '';
		position: absolute;
		top: 0;
		bottom: 0;
		left: 0;
		right: 0;
		opacity: 0.3;
		background-image: url('https://images.unsplash.com/photo-1559056419-266cbf698202?ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&ixlib=rb-1.2.1&auto=format&fit=crop&w=2100&q=80');
		background-size: cover;
		filter: saturate(0);
	}
</style>
