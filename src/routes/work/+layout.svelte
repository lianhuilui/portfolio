<script>
import { page } from "$app/stores"
import 'iconify-icon'
</script>

<slot/>

{#if $page.route.id.startsWith('/work') && $page.route.id != '/work'}
    <a href="/work" class="border-gray-400 border-[1px] py-1 px-2 rounded-md inline-block my-2">
        <iconify-icon icon="ph:caret-left-light"/>
        Back to Portfolio
    </a>
{/if}
