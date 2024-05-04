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
    <h1><a href='/' class="hover-link" on:click|preventDefault={() => scrollToPos(0)}>Nixar <span class="hide-small">Solutions</span></a></h1>
    <div class="spacer"></div>
    <p>
        <a href='/' class="hover-link" on:click|preventDefault={() => scrollToPos(0)}>Home</a><br />
        <a href='/' class="hover-link highlight" on:click|preventDefault={() => scrollTo('about-us')}>About Us</a><br />
        <a href='/' class="hover-link" on:click|preventDefault={() => scrollTo('our-services')}>Our Services</a><br />
    </p>
    <div class="spacer"></div>
    <p>
        <a href='/' class="hover-link" on:click|preventDefault={() => scrollTo('testimonials')}>Testimonials</a><br />
        <a href='/' class="hover-link highlight" on:click|preventDefault={() => scrollTo('faq')}>FAQ</a><br />
        <a href='/' class="hover-link" on:click|preventDefault={() => scrollTo('contact-us')}>Contact Us</a><br />
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

            .hide-small {
                @media screen and (max-width: 500px) {
                    display: none;
                }
            }
        }

        p {
            @include paragraph-md;
        }
    }
</style>