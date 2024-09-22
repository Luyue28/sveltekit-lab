<script>
	import "../app.css";
</script>

<div class="flex flex-col h-screen justify-between">
	<nav class="bg-blue-300">
		<a href="/" class="nav-item"><h1 class="text-xl font-semibold">🐶 Veterinarian</h1></a>
	</nav>

	<main>
		<slot />
	</main>

	<footer class="bg-blue-300">
		<p class="text-center">Made with ❤️ </p>
	</footer>
</div>

<style>
</style>
