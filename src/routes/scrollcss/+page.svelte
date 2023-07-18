<script>
    import {cubicIn, cubicInOut} from 'svelte/easing'
    import Page from "../../components/page.svelte"

    let scroll = 0;
    let height = 0;
    let oHeight = 0;

    let h;

    $: percent = scroll / height;
    $: p = scroll / (h - height)
</script>

<svelte:window bind:scrollY={scroll} bind:innerHeight={height}
    bind:outerHeight={oHeight}
/>

<div bind:clientHeight={h} style={`--percent: ${p ? p : 0}; background: white; width: 100vw; position: absolute; top: 0; left: 0; height: 400vh; z-index: 20;`}>

    <div id="test">
        TESTING
    </div>

    <div style="position: fixed; right: 0; z-index: 30;">
        scroll       {scroll}<br>
            height       {height}<br>
            percent       {percent}<br>
            p       {p}<br>
            h       {h}<br>
    </div>

</div>

<style>
    :global(:root *) {
        /* Pause the animation */
        animation-play-state: paused;
        /* Bind the animation to scroll */
        animation-delay: calc(var(--percent) * -1s);
        /* These last 2 properites clean up overshoot weirdness */
        animation-iteration-count: 1;
        animation-fill-mode: both;
    }

    @keyframes run {
        from {
            top:-10vh;
        }
        10% {
            top: 0vh
        }
        30% {
            top: 0vh
        }
        to {
            top:100vh;
        }
    }
    #test {
        animation-name: run;
        animation-duration: 1s;
        position: fixed;
        background: red;
        width: 100%;
        height: 100%;
    }
</style>
