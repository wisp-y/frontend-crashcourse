<script>
	import { onMount } from 'svelte';

	let date = (new Date()).toLocaleTimeString();

	onMount(() => {
		let interval = setInterval(() => {
			date = new Date().toLocaleTimeString();
		}, 1000);
		return () => {
			clearInterval(interval);
		};
	});
</script>

<h1>Hello World!</h1>
<p class="text-center text-xl font-bold text-slate-600 mt-20">The current time is {date}</p>