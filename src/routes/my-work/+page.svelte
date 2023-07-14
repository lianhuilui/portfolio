<script>
    import { page } from "$app/stores"
    import ImgText from "../../components/imgtext.svelte"

    export let data;
</script>

<h1 class="text-3xl">My Portfolio
    <br>
    <span class="text-sm">as a freelance full-stack developer</span>
</h1>
<hr />

<div class="grid grid-cols-1 md:grid-cols-2 gap-0 sm:gap-2">
    {#each data?.works as work}
        <div>
            {#if work.url}
                <a href={$page.url + work.url}>
                    <ImgText title={work.title} image={work.img} />
                </a>
            {:else}
                    <ImgText title={work.title} image={work.img} />
            {/if}

            {#if work?.tags}
                <div class="flex gap-1 mt-1">
                    {#each work?.tags as tag}
                        <span class="tag">{tag}</span>
                    {/each}
                </div>
            {/if}

            <p class="description">
                {work.description}
            </p>

            {#if work.url}
                <a class="border-gray-400 border-[1px] py-1 px-2 rounded-md inline-block" href={$page.url + work.url}>Read More</a>
            {/if}

            <hr class="h-0 w-8 mx-auto border-2 mb-4 sm:hidden" />
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
