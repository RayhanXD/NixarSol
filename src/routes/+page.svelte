<div class="hero">
    <img src="/red-gradient-background.png" alt="" />
    <section>
        <h1>Welcome to SvelteKit</h1>
        <p>Visit <a href="https://kit.svelte.dev">kit.svelte.dev</a> to read the documentation</p>
    </section>
</div>


<style lang="scss">
    .hero {
        height: 100dvh;
        overflow: clip;

        section {
            height: 100%;
            max-width: calc(1200px + 2rem);
            padding: 0rem 1rem;
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

        img {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            object-fit: cover;
            z-index: -1;
        }
    }
</style>