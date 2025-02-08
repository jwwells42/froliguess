<script>
	const answer = "covfefe";
	let input = $state("");
	let before = $state([]);
	let after = $state([]);
	let message = $state("");
		  
	function check() {	  
		event.preventDefault();
		input = input.toLowerCase();
		
		if (input === answer) {
			message = "COVFEFE";
			before = [];
			after = [];
	  	} else {
			if (input < answer ) {
				before.push(input);
			} else {
				after.push(input);
			}
	  	}
		input = "";
		before.sort();
		after.sort();
		inputField.focus();
	}
</script>

<h1>GUESS THE WORD WHICH MIGHT BE A MEME WORD POTENTIALLY</h1>

{#if before.length > 0}
	<h2>ur word is after:</h2>
	{#each before as wrongup}
		<p>{wrongup}</p>
	{/each}
{/if}
  
<form onsubmit={check}>
	<input bind:value={input} />
	<button type="submit">Submit</button>
</form>

<h1>{message} {message} {message} {message}</h1>
<h1>{message} {message} {message} {message}</h1>
<h1>{message} {message} {message} {message}</h1>
<h1>{message} {message} {message} {message}</h1>
<h1>{message} {message} {message} {message}</h1>
<h1>{message} {message} {message} {message}</h1>
<h1>{message} {message} {message} {message}</h1>
<h1>{message} {message} {message} {message}</h1>
<h1>{message} {message} {message} {message}</h1>
<h1>{message} {message} {message} {message}</h1>

{#if after.length > 0}
	<h2>ur word is before:</h2>
	{#each after as wrongdown}
		<p>{wrongdown}</p>
	{/each}
{/if}

<style>
	:global(body) {
		font-family: 'Courier New', Courier, monospace;
		background: black;
		justify-content: center;
		text-align: center;
	}
	
	h1, h2, p {
		color: white;
	}

	h1 {
		text-shadow: 3px 3px 2px magenta;
	}

	p {
		margin: 0;
	}

	form {
		margin: 2% 0 2%;
	}
</style>