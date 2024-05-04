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
<div class="content">
    <slot /> 
</div>

<style lang="scss">
</style>