<script lang="ts">
    import { Gradient } from "$lib/Gradient";
	import { onMount } from "svelte";

    onMount(() => {
        const gradient = new Gradient();
        // @ts-ignore
        gradient.initGradient('#gradient-canvas');
    });
</script>

<canvas id="gradient-canvas" data-transition-in />
<div class="grain-texture"></div>
<div class="content">
    <section id="home">
        <div class="home-container">
            <h1>Nixar Solutions</h1>
            <div class="bottom-text">
                <p>Social media marketing company <br />Know your potential.</p>
                <p>We help you reach the platform you deserve</p>
                <p>[SCROLL]</p>
            </div>
        </div>
    </section>
    <section id="about-us">
        <div class="section-container"></div>
    </section>
</div>

<style lang="scss">
    .content {
        section {
            .section-container {
                max-width: calc(1200px + 2rem);
                padding: 0rem 2rem;
                margin: auto;
                min-height: 600px;
            }
        }
    
        #home {
            height: 100svh;

            .home-container {
                position: fixed;
                top: 0;
                left: 0;
                right: 0;
                height: 100%;
                min-height: 600px;
                overflow-y: auto;
                max-width: calc(1200px + 2rem);
                padding: 0rem 2rem;
                margin: auto;
                display: flex;
                flex-direction: column;
                justify-content: center;
                align-items: flex-start;
            }
    
            h1 {
                @include title-xl;
    
                @media screen and (max-width: 867px) {
                    transform: translateY(-10%);
                }
    
                @media screen and (max-width: 585px) {
                    transform: translateY(-20%);
                    font-size: 96px;
                }
    
                @media screen and (max-width: 430px) {
                    font-size: 64px;
                }
            }
    
            p {
                @include paragraph-md;
            }
            
            .bottom-text {
                position: fixed;
                padding: 0rem 2rem;
                margin-bottom: 2rem;
                bottom: 2rem;
                left: 0;
                right: 0;
                display: flex;
                justify-content: space-between;
                align-items: flex-end;
                flex-wrap: wrap;
                gap: 2rem;
            }
        }

        #about-us {
            background: $background;
            z-index: 1;
            isolation: isolate;
        }
    }


    #gradient-canvas {
        position: fixed;
        z-index: -2;
        top: 0;
        left: 0;
        width: 100%;
        height: 100%;
        min-height: 600px;
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
</style>