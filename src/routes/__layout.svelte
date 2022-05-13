<div class='container'>
	<slot></slot>
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
	}
	:global(body, h1, h2, h3, h4) {
		margin: 0;
		padding: 0;
	}
  :global(body) {
    background-color: var(--color-bg0_h);
		color: var(--color-fg);
		text-align: center;
  }
	:global(body, input, textarea, select) {
    font-family: "JetBrains Mono", "Ubuntu Mono", Monospace;
	}

  .container {
		text-align: left;
		margin: auto;
		padding: 1rem;
		width: 100%;
    max-width: 800px;
		background-color: var(--color-bg);
  }
</style>