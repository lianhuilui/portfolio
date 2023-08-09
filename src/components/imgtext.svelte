<script>
    export let image = 'http://placehold.co/600x400'
    export let title = '';
</script>                    

<div
    class="w-full aspect-[3/2] relative"
    style="background-image: url({image}); background-size: cover; background-position: center;"
>
    <h2 class="text-2xl bottom-0 right-0 absolute">
        {title}
    </h2>
</div>

<style>
    h2 {
        @apply bg-black text-white;
        @apply px-4;
    }
</style>
