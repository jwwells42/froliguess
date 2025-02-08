<script>
	const answer = "covfefe"; // answer not gonna change so const not let
	let input = $state(""); // the $ thing is called a "rune" in Svelte and it does magic for us
	let before = $state([]); // $state rune itself mean when the variable changes it magics that change into your browser (reactivity)
	let after = $state([]); // and the [] in there means we've got an array we can update 
	let message = $state("");
	let inputField;
		  
	function check() {	  
		event.preventDefault(); // stop you from submitting blank 
		input = input.toLowerCase(); // don't want to think about case sensitivity
		
		if (input === answer) { // single equal sets the variable. double and triple check for sameness but differently
			message = "COVFEFE";
			before = []; // clear the arrays when you get it right
			after = [];
	  	} else {
			if (input < answer ) {
				before.push(input); // put your answer in the before box
			} else {
				after.push(input); // put your answer in the after box
			}
	  	}
		input = ""; // clear input box
		before.sort(); // alphabetize array. love to cast sort without thinking
		after.sort();
		inputField.focus(); // keep cursor in the box so you can guess again without clicking more
	}
</script>

<h1>GUESS THE WORD WHICH MIGHT BE A MEME WORD POTENTIALLY</h1>

{#if before.length > 0} <!-- only show this if you've guessed something up here-->
	<h2>ur word is after:</h2>
	{#each before as wrongup} <!-- means for each word you put in 'before' loop through and make a paragraph thingy-->
		<p>{wrongup}</p>
	{/each}
{/if}
  
<form onsubmit={check}> <!-- when you submit the form it runs check() above in the script part-->
	<input bind:value={input} bind:this={inputField} /> <!-- bind:value is fancy svelte for when you change input, variable updates itself-->
	<button type="submit">Submit</button>
</form>

<!-- hehe -->
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
		width: 90%;
		color: white;
		margin: 0 auto;
	}

	h1 {
		font-size: 2em; /* vw is viewport width, so font size changes with your screen size */ 
		text-shadow: 3px 3px 2px magenta; /* values are horizontal shadow, vertical shadow, blur effect, color */	
	}

	h2 {
		font-size: 1.4em;
	}

	p {
		font-size: 1em;
	}

	form {
		margin: 2% 0 2%; /* gives the input area some margin around it */
	}

	@media (max-width: 600px) {
        :global(body) {
			max-width: 100vw;
			width: 90%;
        }
		h1 { 
			font-size: 0.8em;
		}
		h2, p, form {
			font-size: 0.5em;
		}
    }
</style>