<script>
	import { goto } from '$app/navigation';
	let userInput = '';
	const runCommand = () => {
		const [command, ...args] = userInput.split(' ');
		userInput = '';
		if(command == 'help') {
			goto(command);
		}
		if(command == 'go' && (args[0] ?? false)) {
			goto(args[0]);
		}
	}
</script>

<div id='container'>
	<slot></slot>
	<div id='input-line'>
		<span class='arrow'>➜</span>
		<input on:change={runCommand}
					 bind:value={userInput}
					 type='text'
					 placeholder='help'
					 autofocus>
	</div>
</div>

<style>
  @font-face {
    font-family: "JetBrains Mono";
    src: url('/fonts/mono/JetBrainsMono-Regular.woff2');
  }
	:global(:root) {
		--color-bg: #282828;
		--color-bg0_h: #1d2021;
		--color-fg: #ebdbb2;
		--color-red: #cc241d;
		--color-green: #98971a;
		--color-yellow: #d79921;
		--color-blue: #458588;
		--color-purple: #b16286;
		--color-aqua: #689d6a;
		--color-gray: #a89984;
		--max-width: 800px;
		--font-root: "JetBrains Mono", "Ubuntu Mono", Monospace;
	}
	:global(body, h1, h2, h3, h4) {
		margin: 0;
		padding: 0;
	}
  :global(body) {
    background-color: var(--color-bg0_h);
		color: var(--color-fg);
		display: flex;
		align-items: center;
		justify-items: center;
  }
	:global(body, input, textarea, select, button) {
    font-family: var(--font-root);
	}
  :global(.touched:invalid) {
    border-color: var(--color-red);
    outline-color: var(--color-red);
  }
  :global(.svelte-use-form-hint) {
    font-size: 0.8rem;
    color: var(--color-purple)
  }

  #container {
		text-align: left;
		margin: auto;
		width: 100%;
    max-width: 800px;
    min-height: 100vh;
    background-color: var(--color-bg);
		/*padding-bottom: 2rem;*/
  }
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
    outline: none;
  }
  input:focus {
    border: none;
  }
  #input-line {
    position: fixed;
    bottom: 0;
    width: 100%;
    max-width: 800px;
    display: flex;
    justify-content: center;
    background-color: #3c3836;
  }
  .arrow {
    color: var(--color-aqua);
    line-height: 2rem;
    margin: 0 0.5rem;
  }
</style>