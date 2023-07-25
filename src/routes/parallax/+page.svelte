<script>
    import {onMount} from 'svelte'

    let scroll = 0;
    let height = 0;
    let oHeight = 0;
    let h = 0;

    let code = 'boo';

    let anitext = 'hello world';

    $: percent = scroll / height;
    $: p = scroll / (h - height)

    let animating = false; 

    let imgs = [
        '/head.png',
        '/src/assets/hrcpoints.jpeg',
        'http://placehold.co/1000x1000',
        'http://placehold.co/1000x1000',
        'http://placehold.co/1000x1000',
    ]

    onMount(() => {
        if (document) {
            let html = document.getElementsByTagName('html');
            if (html) {
                code = '<!DOCTYPE html>\n<html lang="en">\n' + html[0].innerHTML + '\n</html>'
            } else {
                code = 'no'
            }
        } else {
            code = 'nodoc'
        }
    })

    function matrix (str) {
        if (!animating) {
            if (str == anitext) return;

            animating = true;

            let current = anitext;

            let p0 = new Promise((resolve, reject) => {
                setTimeout(() => {
                    anitext = current.substr(0, 4);
                    resolve();
                }, 100)
            })
            let p1 = new Promise((resolve, reject) => {
                setTimeout(() => {
                    anitext = current.substr(0, 3);
                    resolve();
                }, 100)
            })
            let p2 = new Promise((resolve, reject) => {
                setTimeout(() => {
                    anitext = current.substr(0, 2);
                    resolve();
                }, 200)
            })
            let p3 = new Promise((resolve, reject) => {
                setTimeout(() => {
                    anitext = current.substr(0, 1);
                    resolve();
                }, 320)
            })
            let p4 = new Promise((resolve, reject) => {
                setTimeout(() => {
                    anitext = str.substr(0, 4);
                    resolve();
                }, 380)
            })
            let p5 = new Promise((resolve, reject) => {
                setTimeout(() => {
                    anitext = str;
                    resolve();
                }, 420)
            })

            Promise.all([p0, p1, p2, p3, p4, p5]).then(() => {
                animating = false;
            })

        }
    }

    function scrolling() {
        /*
        if (p < 0.10) {
            matrix('bye')
        }
        else if (p < 0.20) {
            matrix('hello!')
        }
        */
    }
</script>

<svelte:window bind:scrollY={scroll} bind:innerHeight={height}
    bind:outerHeight={oHeight}
    on:scroll={scrolling}
/>

<div bind:clientHeight={h} style={`--percent: ${p ? p : 0}; --scroll: ${scroll ? scroll : 0}; --percent-delay: 0; background: white; width: 100vw; position: absolute; top: 0; overflow: hidden; left: 0; height: 1000vh; z-index: 20;`}>

    <div id="wwrapper">
        <div id="wrapper">
            <div class="top-layer">
                <div class="text">
                    <span class="hello">
                        Hello.
                    </span>
                    <span class="lian bg-white">
                        I'm Lian.
                    </span>
                </div>
            </div>
            <div class="top-layer">
                <div class="text">I do
                    <p class="inline web">
                        web
                    </p>
                    development
                </div>
            </div>
            <div class="top-layer">
                <div class="text">
                    <span class=''>
                        I&nbsp;
                    </span>
                </div>
                <div class="view">
                    <div class="parallax">
                        <div class="parallax1">
                            <div class="verb">
                                <span>
                                    write&nbsp;
                                </span>
                            </div>
                            <div class="noun">
                                <div>
                                    <span class="bg-yellow-200">
                                        frontend
                                    </span>
                                </div>
                                <div>
                                    <span class="bg-blue-200">
                                        backend
                                    </span>
                                </div>
                            </div>
                            &nbsp;code
                        </div>
                        <div class="parallax2">
                            <div class="verb">
                                <span class="">
                                    use&nbsp;
                                </span>
                            </div>
                            <div class="noun">
                                <div>
                                    <span class="">
                                        Svelte<span class="kit">
                                            <span class="kit-inner">
Kit
                                            </span>
                                        </span>
                                    </span>
                                </div>
                                <div>
                                    <span class="">
                                        node<span class="bg-yellow-400 text-white">&nbsp;JS&nbsp;</span>
                                    </span>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>

    <div id="anitext" style="display: none">
        {anitext}
    </div>

    <div class="code-wrapper">
        <div class="code">
            <code>{code}</code>
        </div>
    </div>

    <div style="padding-top: 0vh; position: absolute; top: 450vh; width: 100vw;" class="flyby text-center">
    </div>

    <div style="padding-top: 0vh; position: absolute; top: 500vh; width: 100vw;" class="flyby text-center">
    </div>

    <div style="padding-top: 0vh; position: absolute; top: 550vh; width: 100vw;" class="flyby text-center">
    </div>

    <div style="padding-top: 0vh; position: absolute; top: 600vh; width: 100vw;" class="flyby text-center">
    </div>

    <div style="padding-top: 0vh; position: absolute; top: 650vh; width: 100vw;" class="flyby text-center">
    </div>

    <div style="padding-top: 0vh; position: absolute; top: 700vh; width: 100vw;" class="flyby text-center">
        <a href="/my-work/">Projects</a>
    </div>

    <div style="padding-top: 0vh; position: absolute; top: 750vh; width: 100vw;" class="flyby text-center">
    </div>

    <div style="padding-top: 0vh; position: absolute; top: 800vh; width: 100vw;" class="flyby text-center">
    </div>

    <div style="padding-top: 0vh; position: absolute; top: 850vh; width: 100vw;" class="flyby text-center">
    </div>

    <div style="padding-top: 0vh; position: absolute; top: 900vh; width: 100vw;" class="flyby text-center">
    </div>

    <div style="padding-top: 0vh; position: absolute; top: 950vh; width: 100vw;" class="flyby text-center">

    </div>

    <div id="picture_wrapper">
        {#each imgs as img}
            <div class="picture">
                <div class="img" style="background-image: url({img})"></div>
            </div>
        {/each}
    </div>

    <div id="percent">
    </div>

    <style>
        #tags {
            margin-top: 20vh;
            animation-name: tags;
            text-align: center;
        }
        @keyframes tags {
            from, 80% { top: 100vh;}
            to, 88% { top: 0vh;}
        }

        .tag {
            animation-name: tag;
            animation-timing-function: ease-in;

            display: inline-block;
            padding: 4px;
            margin-bottom: 4px;
            border-radius: 10px;
            font-size: 30px;

            background:transparent;
        }
        @keyframes tag {
        from, 75%{ transform: translateY(50vh) scale(0.01)}
        85%, to { transform: translateY(0vh) scale(1)}
        }

    </style>

    <div id="tags" style="position: fixed; z-index: 100; height: 100vh; width: 100vw;">
        <div class="tag" style="--percent-delay: 0.01">Svelte/Kit</div>
        <div class="tag" style="--percent-delay: 0.025">Django</div>
        <div class="tag" style="--percent-delay: 0.03">NodeJS</div>
        <div class="tag" style="--percent-delay: 0.06">Express</div>
        <div class="tag" style="--percent-delay: 0.07">Firebase</div>
        <div class="tag" style="--percent-delay: 0.09">Astro</div>
        <div class="tag" style="--percent-delay: 0.08">Joomla</div>
        <div class="tag" style="--percent-delay: 0.03">Shopify</div>
        <div class="tag" style="--percent-delay: 0.02">AngularJS</div>
        <div class="tag" style="--percent-delay: 0.028">Javascript</div>
        <div class="tag" style="--percent-delay: 0.015">Typescript</div>
        <div class="tag" style="--percent-delay: 0.02">Google Cloud Platform</div>
        <div class="tag" style="--percent-delay: 0.075">CSS</div>
        <div class="tag" style="--percent-delay: 0.04">.NET</div>
        <div class="tag" style="--percent-delay: 0.06">Firebase</div>
        <div class="tag" style="--percent-delay: 0.068">jQuery</div>
    </div>

</div>

<style lang="postcss">
    :global(:root) {
        --fontsize: 40px;
        --lineheight: 1.5;
        --headerpadding: 2vh;
        --headerpadding-x: 2vh;
        --oldpicturesize: calc(100vh - (var(--headerpadding-x) * 2 + var(--fontsize)));
        --picturesize: 100vh;
    }

    :global(:root *) {
        animation-timing-function: cubic-bezier();
        /* Pause the animation */
        animation-play-state: paused;
        /* Bind the animation to scroll */
        animation-delay: calc(calc(var(--percent) * -1s) + calc(var(--percent-delay) * 1s));
        /* These last 2 properites clean up overshoot weirdness */
        animation-iteration-count: 1;
        animation-fill-mode: both;
        animation-duration: 1s;
    }

    @keyframes top {
    from { transform: translateY(0); }
    10% { transform: translateY(0); }
    20% { transform: translateY(calc(-1 * var(--lineheight) * var(--fontsize))); }
    30% { transform: translateY(calc(-2 * var(--lineheight) * var(--fontsize))); }
    65% { transform: translateY(calc(-2 * var(--lineheight) * var(--fontsize))); }
    70% { transform: translateY(calc(-3 * var(--lineheight) * var(--fontsize))); }
    to { transform:  translateY(calc(-3 * var(--lineheight) * var(--fontsize))); }
    }

    @keyframes parallax {
    from { transform: translateY(0); }
    35% { transform: translateY(0); }
    40% { transform: translateY(0); }
    50% { transform: translateY(calc(-1 * var(--lineheight) * var(--fontsize))); }
    to { transform: translateY(calc(-1 * var(--lineheight) * var(--fontsize))); }
    }

    @keyframes noun {
    from { transform: translateY(0); }
    30% { transform: translateY(0); }
    40% { transform: translateY(calc(-1 * var(--lineheight) * var(--fontsize))); }
    50% { transform: translateY(calc(-1 * var(--lineheight) * var(--fontsize))); }
    60% { transform: translateY(calc(-2 * var(--lineheight) * var(--fontsize))); }
    to { transform: translateY(calc(-2 * var(--lineheight) * var(--fontsize))); }
    }

    @keyframes noun2 {
    from { transform: translateY(0); }
    55% { transform: translateY(0); }
    60% { transform: translateY(calc(-1 * var(--lineheight) * var(--fontsize))); }
    65% { transform: translateY(calc(-1 * var(--lineheight) * var(--fontsize))); }
    to { transform: translateY(calc(-1 * var(--lineheight) * var(--fontsize))); }
    }

    /* animation */
    #wrapper { animation-name: wrapper; }
    .top-layer { animation-name: top; }
    .parallax { animation-name: parallax; }
    .parallax1 .noun { animation-name: noun; }
    .parallax2 .noun { animation-name: noun2; }

    /* styles */

    #wwrapper {
        animation-name: wwrapper;
        white-space: nowrap;
        padding: var(--headerpadding) var(--headerpadding-x);
        background: transparent;
        z-index: 10;
        position: fixed;
        width: auto;
        top: 50%;
        left: 50%;
        transform: translateY(-50%) translateX(-50%);
    }
    #wrapper {
        position: relative;
        display:block;
        line-height: calc(var(--lineheight) * var(--fontsize));
        height: calc(var(--lineheight) * var(--fontsize));
        overflow-y: hidden;
        background: white;
    }
    .top-layer {
        display: flex;
        justify-content: center;
    }
    .text, .view {
        font-size: var(--fontsize);
        display: block;
        line-height: calc(var(--lineheight) * var (--fontsize));
        overflow: hidden;
    }
    .code-wrapper code {
        font-family: Consolas, "Courier New", monospace;
        font-size: 11px;
        line-height: 0px!important;
        color: #eee;
        user-select: none;
    }
    .parallax {
        display: flex;
        flex-direction: column;
    }
    .parallax1, .parallax2 {
        height: calc(var(--fontsize) * var(--lineheight));
        display: flex;
    }
    .noun, .verb {
        display: flex;
        flex-direction: column;
    }
    .text span,
    .noun span,
    .verb span{
        display: inline;
    }
    #percent {
        top: 0;
        width: 100%;
        z-index: 1000;
        text-align: center;
        position: fixed;
    }
    #percent:after {
        counter-reset: per calc(var(--percent) * 100);
        content: counter(per) '%'
    }
    #anitext {
        width: 100vw;
        background: transparent;
        z-index: 10;
        font-size: var(--fontsize);
    }

    /* PICTURE */
    /* animation */
    @keyframes picture {
    from { transform: translateY(calc(1 * var(--picturesize)))}
    10% { transform: translateY(calc(0 * var(--picturesize)))}
    15% { transform: translateY(calc(0 * var(--picturesize)))}
    25% { transform: translateY(calc(-1 * var(--picturesize)))}
    30% { transform: translateY(calc(-1 * var(--picturesize)))}
    35% { transform: translateY(calc(-2 * var(--picturesize)))}
    40% { transform: translateY(calc(-2 * var(--picturesize)))}
    45% { transform: translateY(calc(-3 * var(--picturesize)))}
    55% { transform: translateY(calc(-3 * var(--picturesize)))}
    60% { transform: translateY(calc(-4 * var(--picturesize)))}
    65% { transform: translateY(calc(-4 * var(--picturesize)))}
    70% { transform: translateY(calc(-5 * var(--picturesize)))}
    to { transform: translateY(calc(-5 * var(--picturesize)))}
    }
    .picture {
        animation-name: picture;
        /* animation-timing-function: linear; */
        animation-timing-function: ease-in-out;
    }

    @keyframes picture_wrapper {
        from, 70% { transform: translateY(0)}
        73%, to { transform: translateY(-110vh)}
    }
    #picture_wrapper {
        animation-name: picture_wrapper;
        animation-timing-function: ease-in;
    }

    /* styles */
    #picture_wrapper {
        height: var(--picturesize);
        width: 100vw;
        box-sizing: border-box;
        overflow: hidden;
        z-index: 9;
        position: fixed;
        /* top: max(
            calc(50vh - (var(--scroll) * 1px)),
            0vh
            calc(1 * var(--headerpadding) + calc(var(--fontsize) * var(--lineheight)))
        );*/
        top: 0vh;
    }
    .picture {
        overflow: hidden;
        height: var(--picturesize);
        width: 100%;
        font-size: var(--fontsize);
        background: transparent;
    }
    .picture .img {
        aspect-ratio: 1;
        width: 100%;
        height: var(--picturesize);
        background-size: contain;
        background-repeat: no-repeat;
        background-position: center center;
    }

    /* web */
    @keyframes web {
    from, 18% { @apply text-black; }
    19%, to { @apply text-orange-400; }
    }

    .web {
        color: white;
        animation-name: web;
    }

    @keyframes wrapper {
        from { opacity: 0; }
        2% { opacity: 1; }
        65% { opacity: 1; }
        68% { opacity: 0; }
        to { opacity: 0; }
    }

    /* kit */
    @keyframes kit {
    from, 45% { width: 0px; }
    48%, to { width: 1.25em; }
    }

    .kit {
        color: white;
        display: inline-block!important;
        animation-name: kit;
        height: calc(var(--lineheight));
        vertical-align: top;
        overflow: hidden;
    }

    .kit-inner {
        background: orange;
    }

    /* hello */

    /* lian */
    @keyframes lian {
    from, 8% { opacity: 0}
    10%, to { opacity: 1.0}
    }
    .lian {
        animation-name: lian;
    }

    /* fly by texts */
    .flyby {
        font-size: 5vh;
    }

    /* animation */
    @keyframes flyby {
    from, 30% {
        transform: translateY(100vh)
    }
    to {
        transform: translateY(0)
    }
    }
    .flyby {
        animation-name: flyby;
        animation-timing-function: linear;
    }
</style>
