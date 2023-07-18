<script lang="ts">
    export let config: Object;
    export let percent: number;

    let value = config.start_value
    let style = config?.init_style ? config.base_style + config.init_style : `display: none;`

    $: {
        let applied = false

        style = config.base_style

        for (let i = 0; i < config.animations.length; i++) {
            let anim_part = config.animations[i]

            if (percent >= anim_part.start_time && percent < anim_part.end_time) {
                if (anim_part.start_value == anim_part.end_value) {
                    value = `${anim_part.start_value}${anim_part.unit}`
                    console.log ('constant style applied')
                } else {

                    let current_time = (percent - anim_part.start_time) / (anim_part.end_time - anim_part.start_time)

                    value = `${anim_part.start_value}${anim_part.unit} + (${anim_part.easing(current_time) * (anim_part.end_value - anim_part.start_value)}${anim_part.unit})`

                    style += `${anim_part.style}: calc(${value});`
                    console.log ('conditional style applied')

                    if (!applied) {
                        style += `--percent: ${current_time}`
                    }
                }


                applied = true
            }
        }

        if (!applied) {
            style += config.init_style;
            console.log ('base style applied')
        }
    }
</script>

<div style={style}>
    <div style='position: absolute; top: 0;'>
    PAGE: {JSON.stringify(config)}
    PERCENT: {JSON.stringify(percent)}
    style: {JSON.stringify(style)}

    </div>
    <slot/>

</div>
