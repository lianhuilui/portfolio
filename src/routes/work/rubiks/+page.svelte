<style>
    .styles button {
        @apply my-2 py-2 px-4 border-[1px] border-gray-400 rounded-md;
    }
</style>

<script>
    let src = "/john.jpg"
    let desc = "Original Image"

</script>

<h1>Rubik Art Generator</h1>

<img class="w-full" src={src} />

<p class="text-center">{desc}</p>

<div class="styles flex mx-auto w-fit">

    <button on:click={() => {src = "/john.jpg"; desc = "Original Image"}}>
        Source Image
    </button>
    <button on:click={() => {src = "/john0.png"; desc = "Floyd-Steinberg dithering, All 6 colors"}}>
        Style 1
    </button>

    <button on:click={() => {src = "/john1.png"; desc = "Floyd-Steinberg, no green"}}>
        Style 2
    </button>

    <button on:click={() => {src = "/john2.png"; desc = "Patterned dithering, nearest gray-value"}}>
        Style 3
    </button>

    <button on:click={() => {src = "/john3.png"; desc = "Patterned dithering, nearest gray-value, blue and white"}}>
        Style 4
    </button>

</div>

<h2>Introduction</h2>

<p>
    This is a passion project. I made it to aid in the design of art piece for my wall.
</p>

<h3>Features</h3>

<ul style="padding-left: 18px; list-style-type: circle;">
    <li>Dithering Modes: Floyd-Steinberg, Patterned, or None</li>
    <li>Multiple color pallettes</li>
    <li>Scale Image responsively</li>
    <li>Calculate Number of Rubik's Cube needed</li>
    <li>Performant</li>
    <li>Screencast-mode: Live processing of application window or desktop screen</li>
</ul>
     
<a href="https://lianhuilui.github.io/rubiksim/" class="block w-fit py-2 px-4 rounded-md border-[1px] border-gray-400 my-2" target="_blank">
    Try the App
</a>
