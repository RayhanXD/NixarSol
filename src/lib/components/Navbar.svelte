<nav>
    <h1><a href='#top' class="hover-link">Nixar Solutions</a></h1>
    <div class="spacer"></div>
    <p>
        <a href='#top' class="hover-link">Home</a><br />
        <a href='#about-us' class="hover-link">About Us</a><br />
        <a href='#our-services' class="hover-link">Our Services</a><br />
    </p>
    <div class="spacer"></div>
    <p>
        <a href='#testimonials' class="hover-link">Testimonials</a><br />
        <a href='#faq' class="hover-link">FAQ</a><br />
        Contact Us<br />
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
    }
</style>