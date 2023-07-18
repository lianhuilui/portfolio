<script>
    import {cubicIn, cubicInOut} from 'svelte/easing'
    import Page from "../../components/page.svelte"

    let scroll = 0;
    let height = 0;
    let oHeight = 0;

    $: percent = scroll / height;

    let config1 = {
        init_style: 'top: 100vh;',
        base_style: 'position: fixed; width: 100%; height: 100%;',
        animations: [
            {
                start_time : 0.25,
                end_time : 1.0,
                start_value : 100,
                end_value : 0,
                easing : cubicInOut,
                style: 'top',
                unit : 'vh'
            },
            {
                start_time : 0.25,
                end_time : 1.0,
                start_value : 0,
                end_value : 1,
                easing : cubicInOut,
                style: 'opacity',
                unit : ''
            },
            {
                start_time : 1.0,
                end_time : 2.0,
                start_value : 0,
                end_value : 0,
                easing : cubicInOut,
                style: 'top',
                unit : 'vh'
            },
            {
                start_time : 2.0,
                end_time : 2.5,
                start_value : 0,
                end_value : -100,
                easing : cubicIn,
                style: 'top',
                unit : 'vh'
            },
            {
                start_time : 2.0,
                end_time : 2.5,
                start_value : 1,
                end_value : 0,
                easing : cubicIn,
                style: 'opacity',
                unit : ''
            },
        ]
    }

    let config2 = {
        init_style: 'top: 100vh;',
        base_style: 'position: fixed; width: 100%; height: 100%;',
        animations: [
            {
                start_time : 2.5,
                end_time : 3.0,
                start_value : 100,
                end_value : 0,
                easing : cubicInOut,
                style: 'top',
                unit : 'vh'
            },
            {
                start_time : 3.0,
                end_time : 4.0,
                start_value : 0,
                end_value : 0,
                easing : cubicInOut,
                style: 'top',
                unit : 'vh'
            },
            {
                start_time : 4.0,
                end_time : 4.5,
                start_value : 0,
                end_value : -100,
                easing : cubicIn,
                style: 'top',
                unit : 'vh'
            },
        ]
    }

</script>

<svelte:window bind:scrollY={scroll} bind:innerHeight={height}
    bind:outerHeight={oHeight}
/>

<div style="background: white; width: 100vw; position: absolute; top: 0; left: 0; height: 1000vh; z-index: 20;">

    <Page config={config1} {percent}>
        <div class="bg-gray-500 h-full w-full" style="">
        HI THERE!
        </div>
    </Page>
    <Page config={config2} {percent}>
        <div class="bg-red-500 h-full w-full" style="">
        HI THERE!
        </div>
    </Page>

    <div style="position: fixed; right: 0; z-index: 30;">
        scroll       {scroll}
    </div>

</div>
