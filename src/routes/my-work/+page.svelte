<script>
	export let data;
</script>

<h1 class="text-3xl">My Freelance Work</h1>
<hr />

<div class="grid grid-cols-1 sm:grid-cols-2 md:grid-cols-3 gap-0 sm:gap-2">
	{#each data?.works as work}
		<div>
			<div
				class="w-full aspect-[3/2] relative"
				style="background-image: url('http://placehold.co/600x400'); background-size: 100%;"
			>
				<h2 class="text-2xl bottom-2 right-4 absolute">
					{work.title}
				</h2>
			</div>

			{#if work?.tags}
				<div class="flex gap-1 mt-1">
					{#each work?.tags as tag}
						<span class="tag">{tag}</span>
					{/each}
				</div>
			{/if}

			<p class="description">
				Lorem ipsum dolor sit amet consectetur adipisicing elit. Deserunt,
				officiis similique, quibusdam voluptatem sapiente alias consequatur
				tempora, voluptatibus dicta saepe cumque nihil! Corporis libero laborum
				est quos impedit laboriosam voluptatibus.
			</p>

			<hr class="h-0 w-8 mx-auto border-2 mb-4" />
		</div>
	{/each}
</div>

<style lang="postcss">
	p.description {
		@apply pb-4;
	}
	h1 {
		@apply py-4;
	}
	h2 {
		@apply py-2;
	}
	h1,
	h2 {
		font-family: "Lucida Sans", "Lucida Sans Regular", "Lucida Grande",
			"Lucida Sans Unicode", Geneva, Verdana, sans-serif;
	}
	.tag {
		@apply rounded-sm px-1 border-[1px] border-gray-400 border-solid bg-gray-300;
	}
</style>
