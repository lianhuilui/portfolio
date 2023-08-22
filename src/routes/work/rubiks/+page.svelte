<style>
    .styles button {
        @apply my-2 py-2 px-4 border-[1px] border-gray-400 rounded-md;
    }

    button.selected {
        font-weight: bold;
        @apply bg-yellow-500;
    }
</style>

<script>
    let src = "/john.jpg"
    let desc = "Original Image"

    let selected = 0

</script>

<h1>Rubik Art Generator</h1>

<img class="w-full" src={src}
    alt="John Wick after running through Rubik's Cube Art Generator"/>

<p class="text-center">{desc}</p>

<div class="styles flex mx-auto w-fit">

    <button class:selected={selected == 0} on:click={() => {selected = 0; src = "/john.jpg"; desc = "Original Image"}}>
        Source Image
    </button>
    <button class:selected={selected == 1} on:click={() => {selected = 1; src = "/john0.png"; desc = "Floyd-Steinberg dithering, All 6 colors"}}>
        Style 1
    </button>

    <button class:selected={selected == 2} on:click={() => {selected = 2; src = "/john1.png"; desc = "Floyd-Steinberg, no green"}}>
        Style 2
    </button>

    <button class:selected={selected == 3} on:click={() => {selected = 3; src = "/john2.png"; desc = "Patterned dithering, nearest gray-value"}}>
        Style 3
    </button>

    <button class:selected={selected == 4} on:click={() => {selected = 4; src = "/john3.png"; desc = "Patterned dithering, nearest gray-value, blue and white"}}>
        Style 4
    </button>

</div>

<h2>Introduction</h2>

<p>
    This is a passion project. I built this in order to learn Svelte. This could be used to aid in the design of a Rubik's Cube art piece.
</p>

<h3>Features</h3>

<ul style="padding-left: 18px; list-style-type: circle;">
    <li>Dithering Modes: Floyd-Steinberg, Patterned, or None</li>
    <li>Multiple color pallettes</li>
    <li>Performant, Live Updates</li>
    <li>In-Browser Processing / No server code</li>
    <li>Screencast-mode: Live processing of application window or desktop screen</li>
</ul>
     
<a href="https://github.com/lianhuilui/rubiksim.git" class="inline-block w-fit py-2 px-4 rounded-md border-[1px] border-gray-400 my-2" target="_blank">
    <iconify-icon icon="ph:github-logo-light" class="text-xl align-middle"/>
    Github Repo
</a>
<a href="https://lianhuilui.github.io/rubiksim/" class="inline-block w-fit py-2 px-4 rounded-md border-[1px] border-gray-400 my-2" target="_blank">
    Try the App
</a>
