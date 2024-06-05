<script>
    import "../app.css";
</script>

<style lang="postcss">
	:root {
    }
</style>

<nav class="container mx-auto max-w-3xl text-blue-600 mt-10 px-5">
	<a href="/" class="inline-block mr-5 hover:text-blue-400">home</a>
	<a href="/about" class="inline-block hover:text-blue-400">about</a>
	<a href="/summarize" class="inline-block ml-5 hover:text-blue-400">summarize</a>
</nav>

<slot />