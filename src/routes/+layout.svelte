<script>
	import "../app.css";
</script>

<nav>
	<ul>
		<li><a href="/">Home</a></li>
		<li><a href="/my-work">Work</a></li>
		<li><a href="/contact">Contact Me</a></li>
	</ul>
</nav>

<main>
	<slot />
</main>

<footer class="text-center">&copy; Copyright 2023</footer>

<style lang="postcss">
	footer {
		@apply border-0 border-t-[1px] border-solid border-slate-400;
		@apply py-6;
		@apply px-2;
	}
	main {
		@apply px-2;
	}
	nav {
		@apply border-0 border-b-[1px] border-slate-400 border-solid;
		@apply pt-4;
		@apply text-2xl;
	}
	nav ul {
		@apply flex;
		@apply gap-4;
		@apply px-2;
		@apply m-0;
	}
	li {
		@apply pb-2;
		list-style: none;
	}
	:global(body) {
		@apply m-0;
		@apply p-0;
	}
	a {
		text-decoration: none;
		color: black;
		font-family: "Lucida Sans", "Lucida Sans Regular", "Lucida Grande",
			"Lucida Sans Unicode", Geneva, Verdana, sans-serif;
	}
	li:first-child {
		border-bottom: solid #ff00ff 6px;
	}
</style>
