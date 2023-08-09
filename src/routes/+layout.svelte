<script lang="ts">
    import "../app.css";
    import 'iconify-icon'
    import { fly } from 'svelte/transition'
    import Nav from '../components/nav.svelte'

    let y: number;
    $: sticky = y > 200
</script>

<svelte:window bind:scrollY={y}></svelte:window>

{#if sticky}
<div class="w-full z-10" in:fly={{y: -100}} class:fixed={sticky}>
    <Nav/>
</div>
{/if}

<Nav/>

<main class="mx-auto max-w-5xl">
    <slot />
</main>

<footer class="text-center">&copy; Copyright 2023</footer>

<style lang="postcss">
    :root {
        background: var(--bg-color)
    }
    footer {
        @apply border-0 border-t-[1px] border-solid border-slate-400;
        @apply py-6;
        @apply px-2;
    }
    main {
        @apply px-2;
    }
    :global(body) {
        @apply m-0;
        @apply p-0;
    }
    :global(h1) {
        @apply text-5xl py-3;
    }
    :global(h2) {
        @apply text-4xl py-3;
    }
    :global(h3) {
        @apply text-3xl py-3;
    }
</style>
