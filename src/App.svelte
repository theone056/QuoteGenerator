<script>
    import { onMount } from "svelte";
    let text;
    let author;
    let data;
	let backgroundColor;
	const newQoute = async () => {
		data = await fetch("https://famous-quotes4.p.rapidapi.com/random?category=all&count=1", {
				"method": "GET",
				"headers": {
					"x-rapidapi-host": "famous-quotes4.p.rapidapi.com",
					"x-rapidapi-key": "f5449621c6mshd4428135bbde721p15da43jsn6676733f4a02"
				}
			}).then((x) => x.json());
		text = data[0].text;
		author = data[0].author;
		backgroundColor = selectColor(Math.floor(Math.random() * 10), 10);
    };
    onMount(newQoute);

	function selectColor(colorNum, colors){
		if (colors < 1) colors = 1; // defaults to one color - avoid divide by zero
		return "hsl(" + (colorNum * (360 / colors) % 360) + ",100%,50%)";
	}

	 
</script>

<main style="--backgroundColor:{backgroundColor}">
	<div class="wrapper">
		<div id="quote-box">
			<div id="text">"
				{text}
			</div>
			<div id="author">
			   - {author}
			</div>
			<button id="tweet-quote">Tweet Qoute</button>
			<button id="new-quote" on:click={newQoute}>New Qoute</button>
		</div>
	</div>
</main>

<style>
	main{
		background-color: var(--backgroundColor);
	}
</style>