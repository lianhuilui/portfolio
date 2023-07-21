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
        'http://placehold.co/600x600',
        'http://placehold.co/600x600',
        'http://placehold.co/600x600',
        'http://placehold.co/600x600',
        'http://placehold.co/600x600',
        'http://placehold.co/600x600',
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
                console.log("stopped!")
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

<div bind:clientHeight={h} style={`--percent: ${p ? p : 0}; --scroll: ${scroll ? scroll : 0}; background: white; width: 100vw; position: absolute; top: 0; overflow: hidden; left: 0; height: 1000vh; z-index: 20;`}>

    <div id="wrapper_wrapper">
        <div id="wrapper">
            <div class="top-layer">
                <div class="text bg-red-100">Hello, I'm Lian.</div>
            </div>
            <div class="top-layer">
                <div class="text bg-blue-100">I'm a Web Dev.</div>
            </div>
            <div class="top-layer">
                <div class="text">
                    <span class='bg-blue-100'>
                        I&nbsp;
                    </span>
                </div>
                <div class="view bg-green-100">
                    <div class="parallax">
                        <div class="parallax1">
                            <div class="verb">
                                <span>
                                    do&nbsp;
                                </span>
                            </div>
                            <div class="noun">
                                <span class="bg-yellow-100">
                                    Frontend.
                                </span>
                                <span class="bg-red-100">
                                    Backend.
                                </span>
                            </div>
                        </div>
                        <div class="parallax2">
                            <div class="verb">
                                <span class="bg-orange-100">
                                    use&nbsp;
                                </span>
                            </div>
                            <div class="noun">
                                <span class="bg-blue-100">
                                    Svelte.
                                </span>
                                <span class="bg-yellow-100">
                                    Django.
                                </span>
                                <span class="bg-red-100">
                                    NodeJS.
                                </span>
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

    <div class="top-layer">
        <code>{code}</code>
    </div>

    <div style="padding-top: 0vh; position: absolute; top: 400vh; width: 100vw;" class="flyby text-center">
        CONTACT
    </div>

    <div style="padding-top: 0vh; position: absolute; top: 450vh; width: 100vw;" class="flyby text-center">
        PROJECTS
    </div>

    <div style="padding-top: 0vh; position: absolute; top: 500vh; width: 100vw;" class="flyby text-center">
        LINKS
    </div>

    <div style="padding-top: 0vh; position: absolute; top: 550vh; width: 100vw;" class="flyby text-center">
        THANKS
    </div>

    <div style="padding-top: 0vh; position: absolute; top: 600vh; width: 100vw;" class="flyby text-center">
        FOR
    </div>

    <div style="padding-top: 0vh; position: absolute; top: 650vh; width: 100vw;" class="flyby text-center">
        STOPPING
    </div>

    <div style="padding-top: 0vh; position: absolute; top: 700vh; width: 100vw;" class="flyby text-center">
        BY!
    </div>

    <div style="padding-top: 0vh; position: absolute; top: 750vh; width: 100vw;" class="flyby text-center">
        GOOD
    </div>
    <div style="padding-top: 0vh; position: absolute; top: 800vh; width: 100vw;" class="flyby text-center">
        BYE
    </div>

    <div style="padding-top: 0vh; position: absolute; top: 850vh; width: 100vw;" class="flyby text-center">
        ..
    </div>

    <div style="padding-top: 0vh; position: absolute; top: 900vh; width: 100vw;" class="flyby text-center">
        ...
    </div>

    <div style="padding-top: 0vh; position: absolute; top: 950vh; width: 100vw;" class="flyby text-center">
        END.
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

    <div style="position: fixed; bottom: 0; right: 0; display: fixed; z-index: 30; text-align: right;">
        scroll       {scroll}px<br>
            height       {height}px<br>
            percent       {parseInt(percent * 100)}vh<br>
            p       {parseInt(p * 100)}%<br>
            h       {h}px<br>
    </div>

</div>

<style>
    :global(:root) {
        --fontsize: 50px;
        --lineheight: 1.5;
        --headerpadding: 2vh;
        --headerpadding-x: 2vh;
        --picturesize: calc(100vh - (var(--headerpadding-x) * 2 + var(--fontsize)));
    }

    :global(:root *) {
        animation-timing-function: cubic-bezier();
        /* Pause the animation */
        animation-play-state: paused;
        /* Bind the animation to scroll */
        animation-delay: calc(var(--percent) * -1s);
        /* These last 2 properites clean up overshoot weirdness */
        animation-iteration-count: 1;
        animation-fill-mode: both;
        animation-duration: 1s;
    }

    @keyframes wrapper_wrapper {
    from, 35% {
        transform: translateY(0); 
    }
    40%, to {
        transform: translateY(var(--headerpadding) * 2 + var(--fontsize)); 
    }
    }

    @keyframes top {
    from { transform: translateY(0); }
    5% { transform: translateY(0); }
    10% { transform: translateY(calc(-1 * var(--lineheight) * var(--fontsize))); }
    15% { transform: translateY(calc(-2 * var(--lineheight) * var(--fontsize))); }
    35% { transform: translateY(calc(-2 * var(--lineheight) * var(--fontsize))); }
    40% { transform: translateY(calc(-3 * var(--lineheight) * var(--fontsize))); }
    to { transform: translateY(calc(-3 * var(--lineheight) * var(--fontsize))); }
    }

    @keyframes parallax {
    from { transform: translateY(0); }
    20% { transform: translateY(0); }
    25% { transform: translateY(calc(-1 * var(--lineheight) * var(--fontsize))); }
    to { transform: translateY(calc(-1 * var(--lineheight) * var(--fontsize))); }
    }

    @keyframes noun {
    from { transform: translateY(0); }
    15% { transform: translateY(0); }
    20% { transform: translateY(calc(-1 * var(--lineheight) * var(--fontsize))); }
    25% { transform: translateY(calc(-1 * var(--lineheight) * var(--fontsize))); }
    30% { transform: translateY(calc(-2 * var(--lineheight) * var(--fontsize))); }
    to { transform: translateY(calc(-2 * var(--lineheight) * var(--fontsize))); }
    }

    @keyframes noun2 {
    from { transform: translateY(0); }
    25% { transform: translateY(0); }
    30% { transform: translateY(calc(-1 * var(--lineheight) * var(--fontsize))); }
    35% { transform: translateY(calc(-2 * var(--lineheight) * var(--fontsize))); }
    to { transform: translateY(calc(-2 * var(--lineheight) * var(--fontsize))); }
    }

    /* animation */
    .top-layer { animation-name: top; }
    .parallax { animation-name: parallax; }
    .parallax1 .noun { animation-name: noun; }
    .parallax2 .noun { animation-name: noun2; }

    /* styles */
    /* 346442 */

    #wrapper_wrapper {
        animation-name: wrapper_wrapper;
        padding: var(--headerpadding) var(--headerpadding-x);
        position: fixed;
        top: max(calc(30vh - (var(--scroll) * 1px)), 0px);
        background: transparent;
        z-index: 10;
    }
    #wrapper {
        position: relative;
        top: 50%;
        width: 100vw;
        display:block;
        overflow-y: hidden;
        /*height: calc(var(--lineheight) * var(--fontsize));*/
        height: calc(var(--lineheight) * var(--fontsize));
    }
    .text, .view {
        font-size: var(--fontsize);
        display: block;
        height: calc(var(--lineheight) * var(--fontsize));
        line-height: calc(var(--fontsize) * var(--lineheight));
        overflow: hidden;
    }
    .top-layer code, .top-layer pre {
        font-family: 'Courier New', Courier, monospace;
        color: #eee;
    }
    .top-layer {
        display: flex;
        width: 100%;
        height: auto;
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
        display: block;
    }
    .text span,
    .noun span,
    .verb span{
        display: block;
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
        font-family: monospace;
        background: transparent;
        z-index: 10;
        font-size: var(--fontsize);
        position:fixed;
        top: 10px;
    }

    /* PICTURE */
    /* animation */
    @keyframes picture {
    from { transform: translateY(0)}
    5% { transform: translateY(0)}
    10% { transform: translateY(calc(-1 * var(--picturesize)))}
    15% { transform: translateY(calc(-2 * var(--picturesize)))}
    20% { transform: translateY(calc(-3 * var(--picturesize)))}
    25% { transform: translateY(calc(-4 * var(--picturesize)))}
    30% { transform: translateY(calc(-5 * var(--picturesize)))}
    35% { transform: translateY(calc(-6 * var(--picturesize)))}
    40% { transform: translateY(calc(-7 * var(--picturesize)))}
    to { transform: translateY(calc(-7 * var(--picturesize)))}
    }
    .picture {
        animation-name: picture;
        animation-timing-function: linear;
    }
    /* styles */
    #picture_wrapper {
        z-index: 30;
        height: var(--picturesize);
        width: 100vw;
        box-sizing: border-box;
        overflow: hidden;
        z-index: 9;
        position: fixed;
        top: max(calc(60vh - (var(--scroll) * 1px)),
            calc(2 * var(--headerpadding) + calc(var(--fontsize) * var(--lineheight))));
    }
    .picture {
        overflow: hidden;
        height: var(--picturesize);
        width: 100%;
        font-size: var(--fontsize);
        background: transparent;
    }
    .picture .img {
        width: 100%;
        height: var(--picturesize);
        background-size: cover;
        background-position: center;
    }

    .flyby {
        font-size: 30px;
    }
</style>
