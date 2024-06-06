<script>
	import { API_URL } from "../../settings";

	var res = "...", prompt = "";

	const onSubmit = () => {
		getSummary(prompt).then(result => {
			res = result;
		}).catch(error => {
			res = error.message;
		});
	};

	const getSummary = (prompt) => {
    	const url = API_URL + '/summary/';
		const options = {
			method: 'POST',
			headers: {
				'Content-Type': 'application/json' // this part is important!
			},
			body: JSON.stringify( // must JSON encode request body
				{
					text: prompt
				}
			)
		};
		return fetch(url, options).then(res => res.json()); // returns a Promise
	}
</script>

<h1>Summarize</h1>

<div class="container mx-auto max-w-3xl mt-20 px-5">
	<form on:submit={e => e.preventDefault()} class="mb-10">
		<label for="prompt" class="block text-2xl font-bold mb-3">
			Enter text to summarize
		</label>
		<input 
			type="text" 
			name="prompt" 
			id="prompt" 
			placeholder="..."
			value={prompt}
			class="w-full mb-5 rounded bg-slate-200 p-2"
			on:change={e => prompt = e.target.value}
		/>
		<button 
			class="px-5 py-3 rounded bg-slate-600 text-white block ml-auto"               
			on:click={onSubmit}
		>
			Summarize!
		</button>
	</form>
	<h1 class="text-2xl mb-3 font-bold">
		Result
	</h1>
	<p class="p-2 bg-slate-200 rounded">
		{res}
	</p>
</div>