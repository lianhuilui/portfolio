<script>
import { page } from "$app/stores"
</script>

<nav class="max-w-5xl mx-auto bg-[#fff]">
    <ul class="">
        <li class:active={$page.route.id == '/'}>
            <a href="/">
                <iconify-icon icon="mdi:home" class="sm:hidden text-3xl align-middle"/>
                <span class="hidden sm:inline">
                    Home
                </span>
            </a>
        </li>
        <li class:active={$page.route.id.startsWith('/work')}>
            <a href="/work">
                <iconify-icon icon="mdi:code" class="sm:hidden text-3xl align-middle"/>
                <span class="hidden sm:inline">
                    Projects
                </span>
            </a>
        </li>
        {#if false}
        <li class:active={$page.route.id.startsWith('/tutorials')}>

            <a href="/tutorials">
                <iconify-icon icon="mdi:teach" class="sm:hidden text-3xl align-middle"/>

                <span class="hidden sm:inline">
                    Tutorials
                </span>
            </a>

        </li>
        {/if}
        <li class:active={$page.route.id.startsWith('/contact')}>
            <a href="/contact">
                <iconify-icon icon="mdi:envelope" class="sm:hidden text-3xl align-middle"/>
                <span class="hidden sm:inline">
                    Contact
                </span>
            </a>

        </li>
    </ul>
</nav>

<style lang="postcss">
    nav {
        @apply border-0 border-b-[1px] border-slate-400 border-solid;
        @apply text-2xl;
        background-color: var(--bg-color)
    }
    nav ul {
    /* @apply max-sm:flex-col sm:flex;*/
        @apply flex w-full sm:w-fit justify-around;
        @apply m-0;
    }
    li {
        list-style: none;
        @apply w-full;
    }
    ul li a {
        @apply w-full text-center;
    }
    a {
        display: inline-block;
        @apply px-6;
        @apply py-4;
        text-decoration: none;
        color: var(--text-color);
        font-family: "Lucida Sans", "Lucida Sans Regular", "Lucida Grande",
        "Lucida Sans Unicode", Geneva, Verdana, sans-serif;
    }
    li.active {
        border-bottom: solid #000000 6px;
    }

</style>
