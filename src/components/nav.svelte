<script>
import { page } from "$app/stores"
import { browser } from '$app/environment'

function toggleTheme() {
    if (browser && document) {
        let html = document.getElementsByTagName('html')[0]
        if (html.hasAttribute('dark')) {
            html.removeAttribute('dark')
            localStorage.setItem('theme', 'light');
        } else {
            html.setAttribute('dark', 'true')
            localStorage.setItem('theme', 'dark');
        }

    }
}
</script>

<nav class="w-full mx-auto bg-[#fff]">
    <ul class="w-full">
        <li class:active={$page.route.id == '/'}>
            <a href="/">
                <iconify-icon icon="ph:house-light" class="sm:hidden text-3xl align-middle"/>
                <span class="hidden sm:inline">
                    Home
                </span>
            </a>
        </li>
        <li class:active={$page.route.id.startsWith('/work')}>
            <a href="/work">
                <iconify-icon icon="ph:code-light" class="sm:hidden text-3xl align-middle"/>
                <span class="hidden sm:inline">
                    Projects
                </span>
            </a>
        </li>
        <li class:active={$page.route.id.startsWith('/contact')}>
            <a href="/contact">
                <iconify-icon icon="ph:envelope-simple-light" class="sm:hidden text-3xl align-middle"/>
                <span class="hidden sm:inline">
                    Contact
                </span>
            </a>
        </li>
        <li class="hidden sm:inline flex-grow">
        </li>
        <li>
            <button aria-label="Toggle Theme" on:click={toggleTheme}>
                <span class="theme-light-button">
                    <iconify-icon icon="ph:sun-light" class="text-3xl align-middle"/>
                </span>
                <span class="theme-dark-button">
                    <iconify-icon icon="ph:moon-light" class="text-3xl align-middle"/>
                </span>
            </button>
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
        @apply flex w-full;
        @apply m-0;
    }
    li {
        list-style: none;
        @apply w-full sm:w-fit;
    }
    ul li a, ul li button {
        @apply w-full text-center;
        display: inline-block;
        @apply px-6;
        @apply py-4;
        text-decoration: none;
        color: var(--text-color);
        font-family: "Lucida Sans", "Lucida Sans Regular", "Lucida Grande",
        "Lucida Sans Unicode", Geneva, Verdana, sans-serif;
    }
    li.active {
        border-bottom: solid var(--text-color) 6px;
    }

    nav {
        position: absolute;
        z-index: 3000;
        @apply w-full;
    }

</style>
