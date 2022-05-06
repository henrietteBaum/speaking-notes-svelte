<script>
	import Editor from './components/Editor.svelte';
</script>

<main>
	<Editor />
</main>

<style>
	main {
		text-align: center;
		margin: 0 auto;
	}



	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}
</style>