<script lang="ts">
    import { Gradient } from "$lib/Gradient";
	import { onMount } from "svelte";

    onMount(() => {
        const gradient = new Gradient();
        // @ts-ignore
        gradient.initGradient('#gradient-canvas');
    });
</script>

<div class="hero">
    <canvas id="gradient-canvas" data-transition-in />
    <div class="grain-texture"></div>
    <section>
        <h1>Nixar Solutions</h1>
    </section>
</div>

<style lang="scss">
    .hero {
        height: 100svh;
        position: relative;

        section {
            height: 100%;
            max-width: calc(1200px + 2rem);
            padding: 0rem 2rem;
            margin: auto;
            min-height: 500px;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: flex-start;
    
            h1 {
                @include title-md;
            }
    
        }

        #gradient-canvas {
            position: fixed;
            z-index: -2;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            --gradient-color-1: $primary; 
            --gradient-color-2: $secondary; 
            --gradient-color-3: #5b0101;  
            --gradient-color-4: #140000;
        }

        .grain-texture {
            position: fixed;
            top: 0;
            left: 0;
            right: 0;
            bottom: 0;
            background: url('/grain-texture.png');
            background-repeat: repeat;
            mix-blend-mode: soft-light;
            opacity: 50%;
            z-index: -1;
        }
    }
</style>