<script>
	let userInput = '';
	let history = [];
	const runCommand = () => {
		const [command, ...args] = userInput.split(' ');
		console.log(command, args);
		history = [userInput, ...history].slice(0, 3);
		userInput = '';
	}
</script>

<div id='output'>
	<div id='welcome'>
		<h1>Hi, I'm <span style='color: var(--color-yellow)'>Martin</span></h1>
		<p>Welcome to my homepage.</p>
	</div>
	<div class='history'>
		{#each history as item}{item}<br>{/each}
	</div>
</div>
<div id='input-line'>
	<span class='arrow'>➜</span>
	<input on:change={runCommand} bind:value={userInput} type='text' autofocus placeholder='help'>
</div>

<style>
  input {
    width: 100%;
    margin: 0;
    padding: 0;
    line-height: 2rem;
    background: none;
    border: 0;
    border-radius: 0;
    color: var(--color-fg);
    font-size: 1rem;
    caret-shape: underscore!important;
    outline: none;
  }
  input:focus {
    border: none;
  }
	#welcome {
		text-align: center;
	}
	#input-line {
		margin-top: 1rem;
		display: flex;
		justify-content: center;
	}
	.arrow {
		color: var(--color-aqua);
    line-height: 2rem;
		margin-right: 0.5rem;
	}
</style>