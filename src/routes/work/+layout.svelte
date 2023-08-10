<script>
import { page } from "$app/stores"
</script>

<slot/>

{#if $page.route.id.startsWith('/work') && $page.route.id != '/work'}
    Back to All Projects
{/if}
