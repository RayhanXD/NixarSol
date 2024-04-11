<script lang="ts">
	import Navbar from '$lib/components/Navbar.svelte';

    import '$lib/styles/global.scss';
</script>

<Navbar />
<div class="content">
    <slot /> 
</div>

<style lang="scss">
</style>