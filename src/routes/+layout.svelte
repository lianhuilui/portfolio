<script lang="ts">
    import "../app.css";
    import 'iconify-icon'
    import { fly } from 'svelte/transition'
    import Nav from '../components/nav.svelte'
    import { browser } from '$app/environment'

    let y: number;
    $: sticky = y > 200

    if (browser) {
        if (localStorage.theme === 'dark' || (!('theme' in localStorage) && window.matchMedia('(prefers-color-scheme: dark)').matches)) {
            setTimeout(() => {
                document.documentElement.setAttribute('dark', 'true')
            }, 500)
        } else {
            setTimeout(() => {
                document.documentElement.removeAttribute('dark')
            }, 500)
        }
    }

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
@import url('https://fonts.googleapis.com/css2?family=Noto+Sans+Display:wght@100;400&family=Pacifico&family=Victor+Mono:wght@100&family=Major+Mono+Display&display=swap');

:root {
    background: var(--bg-color);
    color: var(--text-color);
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

:global(:root) {
    font-family: 'Noto Sans Display', sans-serif;
    font-weight: 100;
    --django-color: #0c4b33;
    --nodejs-color: #026e00;
    --svelte-color: #ff3e00;
    --tailwind-color: #38bdf8;
}

:global(html) {
    --bg-color: white;
    --text-color: black;
    --code-color: #eee;
    --transition-duration: 0.5s;
}
:global(html:not(.style-scope)[dark]) {
    --bg-color: black;
    --text-color: white;
    --code-color: #333;
}

</style>
