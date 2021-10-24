<script>
    export let text;
    export let author;
</script>


<div class="wrapper">
    <div id="quote-box">
        <div id="text">"
            {text}
        </div>
        <div id="author">
            - {author}
        </div>
        <button id="tweet-quote">Tweet Qoute</button>
        <button id="new-quote" on:click>New Qoute</button>
    </div>
</div>


<style>
.wrapper{
		height: 100%;
		width: 100%;
		position: fixed;
		
	}

	#quote-box{
		max-width: 500px;
		height: auto;
		padding: 10px 10px;
		border-radius: 10px;
		margin: 10% auto;
		text-align: center;
		background: white;
	}
</style>