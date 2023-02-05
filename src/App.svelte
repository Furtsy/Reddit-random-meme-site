<script>
	import { onMount } from 'svelte';

	export let name;
	
	onMount(async () => {
		await fetch(`https://a.4cdn.org/b/catalog.json`,{
    headers: {
        'access-control-allow-methods':	'GET, OPTIONS',
        'Access-Control-Allow-Origin':	'http://boards.4chan.org',
		'Access-Control-Allow-Headers': '*'
    } })
    .then(res => res.json())
    .then(console.log)
    .catch(console.error);
	})


		let currentImage = 'https://media.discordapp.net/attachments/925397559160209438/1071548807180996749/image.png'
	
		function changeImage() {
			currentImage = `za`;
		}
</script>

<main>
	<h1>Hello {name}!</h1>
	<p>Visit the <a href="https://svelte.dev/tutorial">Svelte tutorial</a> to learn how to build Svelte apps.</p>
	<!-- svelte-ignore a11y-missing-attribute -->
	<!-- <img src={currentImage} /> -->
	<br>
	<button on:click={changeImage}>Resmi Değiştir</button>
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
