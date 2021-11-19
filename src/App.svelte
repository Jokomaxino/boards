<script>
	import ChessBoard from "./ChessBoard.svelte";
	import CheckerBoard from "./CheckerBoard.svelte";
	import DarkMode from "./DarkMode.svelte";
	import Headroom from "svelte-headroom";

	const games = ["chess", "checkers"];
	let currentGame = games[0];
</script>

<Headroom duration="350ms" offset={50} tolerance={5}>
	<DarkMode />
</Headroom>

<main>
	<select class="menu" bind:value={currentGame}>
		{#each games as game}
			<option value={game}>{game}</option>
		{/each}
	</select>

	{#if currentGame == "chess"}
		<h1>Chess</h1>
		<ChessBoard />
	{:else}
		<h1>Checkers</h1>
		<CheckerBoard />
	{/if}
</main>

<style>
	@keyframes para {
		100% {
			background-position: -5000px 20%, -800px 95%, 500px 50%, 1000px 100%,
				400px 0;
		}
	}
	:global(body) {
		height: 100%;
		/* max-height: 600px; */
		width: 1000px;
		background-color: hsla(200, 40%, 30%, 0.4);
		background-image: url("https://78.media.tumblr.com/cae86e76225a25b17332dfc9cf8b1121/tumblr_p7n8kqHMuD1uy4lhuo1_540.png"),
			url("https://78.media.tumblr.com/66445d34fe560351d474af69ef3f2fb0/tumblr_p7n908E1Jb1uy4lhuo1_1280.png"),
			url("https://78.media.tumblr.com/8cd0a12b7d9d5ba2c7d26f42c25de99f/tumblr_p7n8kqHMuD1uy4lhuo2_1280.png"),
			url("https://78.media.tumblr.com/5ecb41b654f4e8878f59445b948ede50/tumblr_p7n8on19cV1uy4lhuo1_1280.png"),
			url("https://78.media.tumblr.com/28bd9a2522fbf8981d680317ccbf4282/tumblr_p7n8kqHMuD1uy4lhuo3_1280.png");
		background-repeat: repeat-x;
		background-position: 0 20%, 0 100%, 0 50%, 0 100%, 0 0;
		background-size: 2500px, 800px, 500px 200px, 1000px, 400px 260px;
		animation: 50s para infinite linear;
	}
	:global(body.dark-mode) {
		background-color: #1d3040;
	}
	main {
		text-align: center;
		padding: 1em;
		margin: auto;
	}

	h1 {
		color: #ff3e00;
		text-transform: uppercase;
		font-size: 4em;
		font-weight: 100;
	}
	.menu {
		--border: 3px solid blue;
		--borderRadius: 10px;
		--placeholderColor: blue;
	}
</style>
