<script>
import { page } from "$app/stores"
import 'iconify-icon'
</script>

{#if $page.route.id.startsWith('/work') && $page.route.id != '/work'}
    <a href="/work" class="block border-gray-400 border-[1px] py-1 px-2 rounded-md my-2 w-fit">
        <iconify-icon icon="ph:caret-left-light"/>
        Back to Portfolio
    </a>
{/if}

<slot/>

