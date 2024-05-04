<script lang='ts'>
    export let scrollStore;

    let scroll: any;

    scrollStore.subscribe((v: any) => {
        scroll = v;
    })

    const scrollTo = (id: string) => {
        scroll.scrollTo(document.getElementById(id));
    }

    const scrollToPos = (pos: number) => {
        scroll.scrollTo(pos);
    }
</script>

<nav data-scroll data-scroll-sticky data-scroll-target="#scroll-container">
    <h1><a href='#top' class="hover-link" on:click|preventDefault={() => scrollToPos(0)}>Nixar Solutions</a></h1>
    <div class="spacer"></div>
    <p>
        <a href='#top' class="hover-link" on:click|preventDefault={() => scrollToPos(0)}>Home</a><br />
        <a href='#about-us' class="hover-link" on:click|preventDefault={() => scrollTo('about-us')}><span class="highlight">About Us</span></a><br />
        <a href='#our-services' class="hover-link" on:click|preventDefault={() => scrollTo('our-services')}>Our Services</a><br />
    </p>
    <div class="spacer"></div>
    <p>
        <a href='#testimonials' class="hover-link" on:click|preventDefault={() => scrollTo('testimonials')}>Testimonials</a><br />
        <a href='#faq' class="hover-link" on:click|preventDefault={() => scrollTo('faq')}><span class="highlight">FAQ</span></a><br />
        <a href='#contact-us' class="hover-link" on:click|preventDefault={() => scrollTo('contact-us')}>Contact Us</a><br />
    </p>
</nav>

<style lang="scss">
    nav {
        z-index: 2;
        position: fixed;
        width: 100%;
        height: auto;
        margin-top: 0.5rem;
        padding: 1rem;
        display: flex;
        gap: 1rem;
        align-items: flex-start;

        .spacer {
            flex-grow: 2;
        }

        h1 {
            @include title-xs;
        }

        p {
            @include paragraph-md;
        }
        .highlight {
            color: $accent;
        }
    }
</style>