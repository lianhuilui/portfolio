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

<div bind:clientHeight={h} style={`--percent: ${p ? p : 0}; background: white; width: 100vw; position: absolute; top: 0; left: 0; height: 1000vh; z-index: 20;`}>

    <div id="test">
        <div class="text">
            Get
        </div>
        <div class="view">
            <div class="parallax">
                    100%
                <br>
                    10%
                <br>
                    50%
                <br>
                    100%
            </div>
        </div>
    </div>

    <div id="percent">
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
        top:50vh;
    }
    50% {
        top:0vh;
    }
    top {
        top:0vh;
    }
    }

    @keyframes parallax {
    from {
        transform: translateY(0);
    }
    5% {
        transform: translateY(0px);
    }
    10% {
        transform: translateY(calc(-1 * var(--fs)));
    }
    15% {
        transform: translateY(calc(-1 * var(--fs)));
    }
    20% {
        transform: translateY(calc(-2 * var(--fs)));
    }
    25% {
        transform: translateY(calc(-2 * var(--fs)));
    }
    30% {
        transform: translateY(calc(-3 * var(--fs)));
    }
    to {
        transform: translateY(calc(-3 * var(--fs)));
    }
    }

    .text, .view {
        --fs: 100px;
        font-size: var(--fs);
        display: inline-block;
        padding: 0;
        height: 1em;
        line-height: 1em;
        margin: 0;
        overflow: hidden;
        color: white;
    }

    .parallax {
        animation-name: parallax;
        animation-duration: 1s;
    }
    #percent {
        bottom: 0;
        width: 100%;
        text-align: center;
        position: fixed;
    }
    #percent:after {
        counter-reset: per calc(var(--percent) * 100);
        content: counter(per) '%'
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
