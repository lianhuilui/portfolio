<script>
    export let image = 'http://placehold.co/600x400'
    export let title = '';
</script>                    

<div
    class="w-full aspect-[3/2] relative"
    style="background-image: url({image}); background-size: 100%;"
>
    <h2 class="text-2xl bottom-2 right-4 absolute">
        {title}
    </h2>
</div>
