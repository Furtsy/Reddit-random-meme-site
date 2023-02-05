<script>
	export let name;
	const randomImage = (async () => {
var subreddits = ["TurkeyJerky", "KGBTR", "bgy", "duznamemes", "kucukinsanlaryoutube", "lanetliyorumlar", "ShitpostTC", "tamamahbapengelli", "ZargoryanGalaksisi"];
var  subreddit  =  Math.floor(Math.random() * (subreddits.length - 0 + 1 ) + 0 )
var types = ["hot", "new", "top"];
var  type  =  Math.floor(Math.random() * (types.length - 0 + 1 ) + 0 )
var times = ["hour", "day", "week", "month", "year", "all"];
var  time  =  Math.floor(Math.random() * (times.length - 0 + 1 ) + 0 )
		const response = await fetch(`https://www.reddit.com/r/${subreddits[subreddit]}.json?sort=${types[type]}&t=${times[time]}`);
		const data = await response.json();
		const allowed =  data.data.children.filter(post => post.data.post_hint === 'image')
        const randompost = Math.floor(Math.random() * allowed.length)
		return allowed[randompost]
	})()
	
		async function changeImage() {
			document.getElementById("myImg").src = await randomImage.data.url;
		}
</script>

<main>
	<h1>Reddit Random Image</h1>

	<br>
	{#await randomImage}
	<p>...waiting</p>
{:then data}
	<!-- svelte-ignore a11y-img-redundant-alt -->
	<!-- svelte-ignore a11y-click-events-have-key-events -->
	<img on:click={() => window.location.href = data.data.url} src={data.data.url} alt="reddit img" style="display: block; margin: 0 auto;"/>
{:catch error}
	<p>failed to load!</p>
{/await}
<br><br>
<button on:click={() => location.reload()}>New Image</button>
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
