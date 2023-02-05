<script>
	import { onMount } from "svelte";
	export let name;
	let data;
	
	onMount(async () => {
		data = await fetch('https://a.4cdn.org/b/catalog.json')
.then(response => response.json())
console.log(data)
	})


		let currentImage = 'https://media.discordapp.net/attachments/925397559160209438/1071548807180996749/image.png'
	
		function changeImage() {
			currentImage = `za`;
		}
</script>


<script context="module">
	export async function load({ fetch }) {
	  const res = await fetch('https://a.4cdn.org/b/catalog.json');
	  const articles = await res.json() ;
	  console.log(articles)
	if (res.ok) return { props: { articles: articles } };
	return {
	  status: res.status,
	  error: new Error()
	 };
	}
  </script>

<main>
	<h1>Hello {name}!</h1>
	<p>Visit the <a href="https://svelte.dev/tutorial">Svelte tutorial</a> to learn how to build Svelte apps.</p>
	<!-- svelte-ignore a11y-missing-attribute -->
	<!-- <img src={currentImage} /> -->
	<br>
	<button on:click={changeImage}>Resmi Değiştir</button>
	<pre>
		{JSON.stringify(data, null, 2)}
	</pre>
</main>


<style>
	:global(body) {
		background-color: #1d3040;
		color: #bfc2c7;
	}
	main {
		text-align: center;
		padding: 1em;
		max-width: 240px;
		margin: 0 auto;
	}

	h1 {
		color: #ff3e00;
		text-transform: uppercase;
		font-size: 4em;
		font-weight: 100;
	}
	
	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}

</style>
