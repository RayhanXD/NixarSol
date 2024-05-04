<script lang="ts">
	import Navbar from '$lib/components/Navbar.svelte';

    import '$lib/styles/global.scss';
    import '$lib/styles/locomotive-scroll.scss';
	import { setContext } from 'svelte';
	import { writable } from 'svelte/store';
    
    const scrollStore = writable(null);
    setContext('locomotive-scroll', {
        scrollStore
    });
</script>

<Navbar {scrollStore} />
<div class="content" data-sveltekit-preload-data="hover" data-scroll-container id="scroll-container">
    <slot /> 
</div>
<canvas id="gradient-canvas"/>
<div class="grain-texture"></div>

<style lang="scss">
    #gradient-canvas {
		position: fixed;
		z-index: -2;
		top: 0;
		left: 0;
		width: 100vw;
        height: 100vh;
		--gradient-color-1: $primary;
		--gradient-color-2: $secondary;
		--gradient-color-3: #5b0101;
		--gradient-color-4: #140000;
	}

	.grain-texture {
		position: fixed;
		top: 0;
		left: 0;
		width: 100vw;
        height: 100vh;
		background: url('/grain-texture.png');
		background-repeat: repeat;
		mix-blend-mode: soft-light;
		opacity: 50%;
		z-index: -1;
	}
</style>