<nav>
    <h1>Nixar Solutions</h1>
    <div class="spacer"></div>
    <p>Home</p>
    <p>About Us</p>
    <p>Our Services</p>
    <p>Testimonials</p>
    <p>Contact Us</p>
    <p>FAQs</p>
</nav>

<style lang="scss">
    nav {
        z-index: 2;
        position: fixed;
        width: 100%;
        height: 4rem;
        padding: 1rem;
        display: flex;
        gap: 1rem;
        align-items: center;
        background: rgba(0, 0, 0, 0.1);
        backdrop-filter: blur(8px);
        box-shadow: 0px 5px 10px rgba(0, 0, 0, 0.1);

        .spacer {
            flex-grow: 2;
        }

        h1 {
            @include title-xs;
        }

        p {
            font-weight: 500;
        }
    }
</style>