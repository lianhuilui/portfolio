<script>
    import {onMount} from 'svelte'
    import 'iconify-icon'
    import { browser } from '$app/environment'

    let scroll = 0;
    let height = 0;
    let oHeight = 0;
    let h = 0;

    let light = false;

    let code = '';

    let loop_paused = false;

    let anitext = 'hello world';

    $: percent = scroll / height;
    $: p = scroll / (h - height)

    let animating = false; 

    let imgs = [
    ]

    onMount(() => {
        if (document) {
            let html = document.getElementsByTagName('html');
            if (html) {
                code = '<!DOCTYPE html>\n<html lang="en">\n' + html[0].innerHTML + '\n</html>'
            } else {
                code = ''
            }
        } else {
            code = ''
        }
    })

    let darkMode;

    if (browser) {
        if (localStorage.theme === 'dark' || (!('theme' in localStorage) && window.matchMedia('(prefers-color-scheme: dark)').matches)) {
            darkMode = true;
            setTimeout(() => {
                document.documentElement.setAttribute('dark', 'true')
            }, 500)
        } else {
            darkMode = false;
            setTimeout(() => {
                document.documentElement.removeAttribute('dark')
            }, 500)
        }
    }

    function toggleTheme() {
        if (browser && document) {
            let html = document.getElementsByTagName('html')[0]
            if (html.hasAttribute('dark')) {
                light = true
                html.removeAttribute('dark')
                localStorage.setItem('theme', 'light');
            } else {
                light = false
                html.setAttribute('dark', 'true')
                localStorage.setItem('theme', 'dark');
            }

        }
    }

</script>

<svelte:window bind:scrollY={scroll} bind:innerHeight={height}
    bind:outerHeight={oHeight}
/>

<div bind:clientHeight={h} style={`--percent: ${p ? p : 0}; --scroll: ${scroll ? scroll : 0}; --percent-delay: 0; transition: background-color var(--transition-duration); background: var(--bg-color); width: 100vw; position: absolute; top: 0; overflow: hidden; left: 0; height: 1000vh; z-index: 120;`}>

    <nav style="position: fixed; left: 0; width: 100vw" class="flex justify-between">
        <a href="#">
            Home
        </a>
        <a href="/work">
            Projects
        </a>
        <a href="#">
            Contact
        </a>
        <button on:click={toggleTheme}>
            {#if light}
                <iconify-icon icon="mdi:lightbulb"/> Dark Mode
            {:else}
                <iconify-icon icon="mdi:lightbulb-on"/> Light Mode
            {/if}
        </button>
    </nav>

    <div id="wwrapper">
        <div id="wrapper">
            <div>
                <p>Hi, I'm Lian.</p>
                <p>I'm an experienced 
                    <span class="highlight" style="--percent-delay: 0.12; --highlight-text-color: white; --highlight-text-color: black;">full-stack</span> web developer.</p>

                <p>I enjoy building backends with
                    <span class="highlight" style="--percent-delay: 0.21; --highlight-text-color: white; --highlight-color: var(--django-color);">Django</span>,
                    <span class="highlight" style="--percent-delay: 0.23; --highlight-text-color: white; --highlight-color: var(--nodejs-color);">NodeJS</span>, and
                    <span class="highlight" style="--percent-delay: 0.25; --highlight-text-color: white; --highlight-color: var(--svelte-color);">SvelteKit</span>
                </p>

                <p>and user interfaces with 

                    <span class="highlight" style="--percent-delay: 0.31; --highlight-text-color: white; --highlight-color: var(--tailwind-color);">Tailwind</span> and
                    <span class="highlight" style="--percent-delay: 0.33; --highlight-text-color: white; --highlight-color: var(--svelte-color);">Svelte.</span>

                </p>

            </div>
        </div>
    </div>

    <div id="scroll-helper" class="hide-after-scroll">
        <span>Scroll Down
            <br>
            <iconify-icon icon="material-symbols:arrow-circle-down" class="text-3xl align-middle bounce"/>
        </span>
    </div>

    <div class="code-wrapper">
        <div class="code">
            <code class="">{code}</code>
            <code class="hidden xl:inline">{code}</code>
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
    </div>

    <div style="padding-top: 0vh; position: absolute; top: 750vh; width: 100vw;" class="flyby text-center">
    </div>

    <div style="padding-top: 0vh; position: absolute; top: 800vh; width: 100vw;" class="flyby text-center">
    </div>

    <div style="padding-top: 0vh; position: absolute; top: 850vh; width: 100vw;" class="flyby text-center">
    </div>

    <div style="z-index: 30; padding-9op: 0vh; position: absolute; top: 650vh; width: auto" class="flyby text-center">

        <div class="hidden" style=" background: var(--bg-color); top: 0; position: fixed; height: 100vh; width: 100vw; text-align: center; z-index: 1000;">
            <div class=""></div>

        </div>


    </div>

    <div style="z-index: 120; padding-9op: 0vh; position: absolute; top: 900vh; width: auto" class="flyby text-center">
        <div style="transition: background-color var(--transition-duration); background: var(--bg-color); top: 0; position: fixed; height: 100vh; width: 100vw; text-align: center;">
            <div class="flex flex-col h-full pt-4">

                <div class="text-2xl pt-8 pb-4">
                    See All Projects
                </div>

                <hr style="border-width: 2px; width: 20px; margin: 0 auto;">

                <div class="flex flex-col justify-around w-auto mx-auto flex-grow">
                    <span style="">
                        <iconify-icon icon="heroicons-solid:mail" class="text-5xl align-middle"></iconify-icon>
                        <br>
                        <span class="text-2xl align-middle">e-mail me</span>
                    </span>
                    <span style="">
                        <iconify-icon icon="fa-brands:linkedin" class="text-5xl align-middle"></iconify-icon>
                        <br>
                        <span class="text-2xl align-middle">linkedin</span>
                    </span>
                    <span style="">
                        <iconify-icon icon="heroicons-solid:document-download" class="text-5xl align-middle"></iconify-icon>
                        <br>
                        <span class="text-2xl align-middle">résumé</span>
                    </span>
                </div>

                <div class="text-sm pb-4">
                    <button on:click={() => {window.scrollTo({top: 0, behavior: 'smooth' }); /*scroll = 0*/}}>
                        <iconify-icon icon="material-symbols:arrow-circle-up" class="text-3xl align-middle"></iconify-icon>
                        <br>rewind back
                    </button>
                </div>
            </div>

        </div>

    </div>

    <div id="picture_wrapper">
        {#each imgs as img}
            <div class="picture">
                <div class="img" style="background-image: url({img})"></div>
            </div>
        {/each}
    </div>

    <div id="percent-bar">
    </div>

    <div id="percent">
    </div>

    <div id="tags" style="position: fixed; z-index: 100; height: 100vh; width: 100vw;">
        <h2>Skills:</h2>
        <div class="tag" style="--percent-delay: 0.01">Svelte/Kit</div>
        <div class="tag" style="--percent-delay: 0.09">Python</div>
        <div class="tag" style="--percent-delay: 0.025">Django</div>
        <div class="tag" style="--percent-delay: 0.028">Javascript</div>
        <div class="tag" style="--percent-delay: 0.115">Typescript</div>
        <div class="tag" style="--percent-delay: 0.03">NodeJS</div>
        <div class="tag" style="--percent-delay: 0.06">Express</div>
        <div class="tag" style="--percent-delay: 0.07">Firebase</div>
        <div class="tag" style="--percent-delay: 0.019">PHP</div>
        <div class="tag" style="--percent-delay: 0.08">Joomla</div>
        <div class="tag" style="--percent-delay: 0.11">Shopify</div>
        <div class="tag" style="--percent-delay: 0.02">AngularJS</div>
        <div class="tag" style="--percent-delay: 0.022">SQL</div>
        <div class="tag" style="--percent-delay: 0.08">Google Cloud Platform</div>
        <div class="tag" style="--percent-delay: 0.124">Flutter</div>
        <div class="tag" style="--percent-delay: 0.075">CSS</div>
        <div class="tag" style="--percent-delay: 0.078">Bootstrap</div>
        <div class="tag" style="--percent-delay: 0.082">Tailwind</div>
        <div class="tag" style="--percent-delay: 0.07">HTML</div>
        <div class="tag" style="--percent-delay: 0.038">C#</div>
        <div class="tag" style="--percent-delay: 0.12">.NET</div>
        <div class="tag" style="--percent-delay: 0.06">Firebase</div>
        <div class="tag" style="--percent-delay: 0.068">jQuery</div>
        <div class="tag" style="--percent-delay: 0.11">Git</div>
        <div class="tag" style="--percent-delay: 0.10">Linux</div>
    </div>

    <h1 id="projects-header">Projects Showcase</h1>

    <div id="projects" style="" class="project">

        <div class="text-2xl pt-8 pb-4">Rubik's Cube Art Generator</div>

        <div id="rubiks" class="min-h-[500px] mx-auto aspect-video pausable max-w-5xl w-full relative"
            class:pause_child={loop_paused}
            on:click={() => {loop_paused = !loop_paused}}
        >

            <div class="john w-full h-full"
                style={`
                        background-image: url(/john0.jpg);
                `}>
            </div>
            <div class="john w-full h-full"
                style={`
                        background-image: url(/john1.png);
                `}>
            </div>

        </div>

        <div>
            <p style="max-width: 800px;" class="mx-auto p-4">
                A browser application written in Svelte to convert an image to Rubik's Cube art, drawing an image only using colors from the Rubik's cube.
            </p>

            <a href="/work/rubiks">Read More</a>
        </div>
    </div>

    <div id="projects1" style="" class="project">

        <div class="text-2xl pt-8 pb-4">Loyalty Points App</div>
        <div class="min-h-[500px] mx-auto aspect-video max-w-5xl w-full relative"
            style={`background-image: url(/cafe2.jpg); background-size: cover; background-position: center`}
        >
            <span style="position: absolute; bottom: 0; left: 0;  background: var(--bg-color); opacity: 0.9" class="text-xs w-full text-center py-1">
                Stock Photo by Los Muertos Crew
                <br>
                https://www.pexels.com/photo/photo-of-woman-busy-browsing-through-her-cellphone-7487529/
            </span>
        </div>
        <div>
            <p style="max-width: 800px;" class="mx-auto p-4">
                A Progressive Web App written in Svelte + SvelteKit to boost customer loyalty of a cafe. Customers are able to collect points, top up cash cards, get free drinks, and more.
            </p>
        </div>

    </div>

    <div id="projects2" style="" class="project">
        <div class="text-2xl pt-8 pb-4">Facebook Instant Game</div>

        <div class="min-h-[500px] mx-auto aspect-video max-w-5xl w-full relative"
            style={`background-image: url(/galaxy10mm.jpg); background-size: cover; background-position: center`}
        >
            <span style="position: absolute; bottom: 0; left: 0; background: var(--bg-color); opacity: 0.8" class="text-xs w-full text-center py-1">
                Photo Source: Samsung Myanmar Facebook Page
            </span>
        </div>
        <div>
            <p style="max-width: 800px;" class="mx-auto p-4">
                A Facebook "Instant Game" where users can share what they will be in 10 years.
            </p>
        </div>
    </div>


</div>

    <style>

  @import url('https://fonts.googleapis.com/css2?family=Noto+Sans+Display:wght@100;400&family=Pacifico&family=Victor+Mono:wght@100&family=Major+Mono+Display&display=swap');
    :global(:root) {
        font-family: 'Noto Sans Display', sans-serif;
        font-weight: 100;
        --django-color: #0c4b33;
        --nodejs-color: #026e00;
        --svelte-color: #ff3e00;
        --tailwind-color: #38bdf8;
    }

    :global(html) {
        --bg-color: white;
        --text-color: black;
        --code-color: #eee;
        --transition-duration: 0.5s;
    }
    :global(html:not(.style-scope)[dark]) {
        --bg-color: black;
        --text-color: white;
        --code-color: #333;
    }

    nav {
        background-color: var(--bg-color);
        color: var(--text-color);
        transition: background-color var(--transition-duration), color var(--transition-duration);
    }

    @media (max-width: 320px) {
        :global(:root) {
            --fontsize: 10px;
            --frame-border: 2px;
        }
    }
    @media (min-width: 320px) {
        :global(:root) {
            --fontsize: 12px;
            --frame-border: 2px;
        }
    }
    @media (min-width: 420px) {
        :global(:root) {
            --fontsize: 16px;
        }
    }
    @media (min-width: 550px) {
        :global(:root) {
            --fontsize: 20px;
        }
    }
    @media (min-width: 660px) {
        :global(:root) {
            --fontsize: 24px;
            --frame-border: 4px;
        }
    }
    @media (min-width: 800px) {
        :global(:root) {
            --fontsize: 30px;
        }
    }

    :global(:root *) {
        --lineheight: 1.5;
        --headerpadding: 2vh;
        --headerpadding-x: 2vh;
        --oldpicturesize: calc(100vh - (var(--headerpadding-x) * 2 + var(--fontsize)));
        --picturesize: 100vh;
        color: var(--text-color);
        transition: color var(--transition-duration);
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

    #wwrapper {
        border: var(--frame-border) solid var(--text-color);
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
        padding-left: 4px;
        padding-right: 4px;
        position: relative;
        display:block;
        line-height: calc(var(--lineheight) * var(--fontsize));
        /*height: calc(var(--lineheight) * var(--fontsize));*/
        overflow-y: hidden;
        background: var(--bg-color);
    }
    #wrapper { animation-name: wrapper; }
    @keyframes wrapper {
    from{ opacity: 0; height: 0px; }
    2%,8%  { opacity: 1; height: calc(1* var(--lineheight) * var(--fontsize))}
    10%, 15%  { opacity: 1; height: calc(2* var(--lineheight) * var(--fontsize))}
    20%, 25%  { opacity: 1; height: calc(3* var(--lineheight) * var(--fontsize))}
    30%, 40%  { opacity: 1; height: calc(4* var(--lineheight) * var(--fontsize))}
    42% { opacity: 0; height: calc(0* var(--lineheight) * var(--fontsize))}
    to  { opacity: 0; height: calc(0* var(--lineheight) * var(--fontsize))}
    }

    @keyframes wwrapper {
      from {opacity: 0; }
      2%, 40% {opacity: 1;}
      42%, to { opacity: 0}
    }

    .code-wrapper code {
        font-family: "Major Mono Display", Consolas, "Courier New", monospace;
        text-transform: lowercase;
        font-size: 11px;
        color: var(--code-color);
        transition: color var(--transition-duration);
        user-select: none;
    }
    #percent {
        bottom: 0;
        width: 100vw;
        z-index: 1000;
        text-align: center;
        position: fixed;
    }
    #percent:after {
        counter-reset: per calc(var(--percent) * 100);
        content: counter(per) '%'
    }
    #percent-bar {
        top: 0;
        left: 0;
        width: calc(var(--percent) * 100%);
        z-index: 1000;
        background: orange;
        height: 4px;
        position: fixed;
    }
    #anitext {
        width: 100vw;
        background: transparent;
        z-index: 10;
        font-size: var(--fontsize);
    }
    #wrapper p {
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


    /* fly by texts */
    .flyby {
        font-size: 5vh;
    }

    /* animation */
    @keyframes flyby {
    from, 70% {
        transform: translateY(50vh)
    }
    to {
        transform: translateY(0)
    }
    }
    .flyby {
        animation-name: flyby;
        animation-timing-function: linear;
    }

    #scroll-helper {
        position: fixed;
        top: 0;
        width: 100vw;
        height: 100vh;
    }

    #scroll-helper span {
        position: fixed;
        top: 50%;
        left: 50%;
        transform: translateY(-50%) translateX(-50%);
        width: 100vw;
        text-align: center;
    }

    .hide-after-scroll {
        animation-name: hide-after-scroll;
    }
    @keyframes hide-after-scroll {
    from { opacity: 1; }
    1%, to { opacity: 0; }
    }
    .bounce {
        animation-name: bounce;
        animation-play-state: running;
        animation-iteration-count: infinite;
        animation-duration: 1.6s;
        animation-timing-function: ease-in-out;
    }
    @keyframes bounce {
    0%,  100% {transform: translateY(0);} 
    50% {transform: translateY(-15px);} 
    } 

    nav { 
        z-index: 1000;
        transform: translateY(calc(var(--percent) * -1000% * 0.5));
    }
    nav a, nav button {
        padding: 8px;
    }
    nav {
      animation-name: nav;
    }
    @keyframes nav {
        from { transform: translateY(0)}
        20%, 97% { transform: translateY(calc(-1 * (8px * 2 + 25px + 4px /* margin of error */)))}
        to { transform: translateY(0)}
    }
    #tags {
        margin-top: 20vh;
        animation-name: tags;
        text-align: center;
    }
    @keyframes tags {
    from, 40% { top: 100vh; opacity: 1 }
    45% { top: 0vh }
    65% { opacity: 1}
    70% { opacity: 0}
    87% { top: 0vh }
    88%, to { top: -100vh }
    }

    #projects-header {
      text-align: center;
      animation-name: project-header;
      animation-timing-function: linear;
      position: fixed;
      z-index: 100;
      height: 10vh;
      width: 100vw;
    }
    @keyframes project-header {
    from, 62.1% { top: 100vh }
    to, 71% { top: 0vh }
    }
    .project {
       background: var(--bg-color);
       position: fixed;
       z-index: 100;
       height: 100vh;
       width: 100vw;
    }
  
    #projects {
      border-top: 2px solid var(--text-color);
      animation-name: projects;
      animation-timing-function: linear;
      text-align: center;
      transition: background-color var(--transition-duration);
    }
    #projects1 {
      animation-name: projects1;
      animation-timing-function: linear;
      border-top: 2px solid var(--text-color);
      text-align: center;
      transition: background-color var(--transition-duration);
    }
    #projects2 {
      animation-name: projects2;
      animation-timing-function: linear;
      border-top: 2px solid var(--text-color);
      text-align: center;
      transition: background-color var(--transition-duration);
    }
    @keyframes projects {
    from, 63% { top: 100vh }
    to, 72% { top: 0vh }
    }
    @keyframes projects1 {
    from, 72% { top: 100vh }
    to, 81% { top: 0vh }
    }
    @keyframes projects2 {
    from, 81% { top: 100vh }
    to, 90% { top: 0vh }
    }

    .tag {
        animation-name: tag;
        animation-timing-function: ease-out;
        display: inline-block;
        padding: 4px;
        margin-bottom: 4px;
        border-radius: 10px;
        font-size: 30px;

        background:transparent;
    }
    @keyframes tag {
    from, 44%{ transform: translateY(50vh) scale(0.01)}
    50%, to { transform: translateY(0vh) scale(1)}
    }

    @keyframes highlight {
    from { right: 100%;}
    to, 1% {right: 0%;}
    }
    @keyframes highlight-text {
    from { color: var(--text-color); }
    to, 2% { color: var(--highlight-text-color); }
    }
    .highlight {
        font-weight: normal;
        position: relative;
        padding-left: 4px;
        padding-right: 4px;
        --highlight-color: yellow;

        animation-name: highlight-text;
        animation-play-state: paused;
        animation-delay: calc(calc(var(--percent) * -1s) + calc(var(--percent-delay) * 1s));
        animation-iteration-count: 1;
        animation-fill-mode: both;
        animation-duration: 1s;

    }
    .highlight::before {
        animation-name: highlight;

        animation-play-state: paused;
        animation-delay: calc(calc(var(--percent) * -1s) + calc(var(--percent-delay) * 1s));
        animation-iteration-count: 1;
        animation-fill-mode: both;
        animation-duration: 1s;

        content: "";
        position: absolute;
        background: var(--highlight-color);
        z-index: -1;
        top: 0;
        left: 0;
        bottom: 0;
    }

        #rubiks {
            position: relative;
        }
        .john {
            background-size: cover;
            background-position: center;
            background-repeat: no-repeat;
            position: absolute;
            top: 0;
            left: 0;
        }
        .john-aspect {
            min-height: 400px;
            margin: 0 auto;
        }
        .john-wrapper {
            overflow: hidden;
            display: block;
            animation-name: swipedown;
        }
        .john:nth-child(1) {
        }
        .john:nth-child(2) {
            animation-name: opacity;
            animation-timing-function: cubic-bezier();
            animation-play-state: running;
            animation-duration: 3.7s;
            animation-delay: 0s;
            animation-iteration-count: infinite;
            animation-fill-mode: both;
        }
        @keyframes opacity {
            from { opacity: 0 }
            50% { opacity: 1 }
            to { opacity: 0 }
        }
        @keyframes swipedown {
          from, to { height: 0%; border: 5px solid green}
          50% { height: 100%; border: 5px solid blue}
        }
        .pause_child > * {
            animation-play-state: paused!important;
        }
        .pause_child {
        }
        .pause_child::before {
            content: "paused"!important;
        }
        .pausable::before {
            color: var(--text-color);
            background-color: var(--bg-color);
            content: "click to pause";
            padding: 2px 4px;
            bottom: 0;
            right: 0;
            position: absolute;
            z-index: 2000;
        }

</style>
