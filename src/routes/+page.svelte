<script lang="ts">
	import { Gradient } from '$lib/Gradient';
	import { onMount } from 'svelte';

	let homeText: HTMLDivElement;
	let bottomText: HTMLDivElement;
	let aboutSection: HTMLElement;

	onMount(() => {
		const gradient = new Gradient();
		// @ts-ignore
		gradient.initGradient('#gradient-canvas');

		const homeElements = [
			homeText, bottomText
		];

		const updateHomeVisibility = () => {
			homeElements.forEach((e) => {
				if (aboutSection.getBoundingClientRect().top < e.getBoundingClientRect().top) {
					e.style.visibility = 'hidden'
				}
				else {
					e.style.visibility = 'visible';
				}
			});
		}

		document.addEventListener('scroll', updateHomeVisibility);
		return () => document.removeEventListener('scroll', updateHomeVisibility);
	});
</script>

<canvas id="gradient-canvas" data-transition-in />
<div class="grain-texture"></div>
<div class="content">
	<section id="home">
		<div class="home-container" bind:this={homeText}>
			<div bind:this={homeText}>
				<h1>Nixar Solutions</h1>
				<h2>Know your potential</h2>
			</div>
			<div class="bottom-text" bind:this={bottomText}>
				<p>Social media marketing agency<br />Know your potential.</p>
				<p>We help you reach the platform you deserve.</p>
				<p>[SCROLL]</p>
			</div>
		</div>
	</section>
	<section id="about-us" bind:this={aboutSection}>
		<div class="text-infinite-scroll">
			<h1>About Us —&nbsp;</h1>
			<h1>About Us —&nbsp;</h1>
			<h1>About Us —&nbsp;</h1>
			<h1>About Us —&nbsp;</h1>
			<h1>About Us —&nbsp;</h1>
		</div>
		<div class="section-container">
			<p class="bold">We are Nixar.</p>
			<p>
				A digital marketing agency adapted to the <span class="highlight">needs of the future.</span
				>
			</p>
			<p>
				Together, we can evaluate <span class="highlight">your needs</span> and let you know
				<span class="highlight">your potential.</span>
			</p>
			<p>
				Need exposure? We have you covered with likes, comments, and followers. <span
					class="highlight">Fast.</span
				>
			</p>
			<p>
				Get in <span class="highlight">contact</span> with us to initiate your social media
				<span class="highlight">growth</span> <span class="highlight">today.</span>
			</p>
			<p class="bold">Understanding Challenges.</p>
			<p>
				We navigate digital complexities to <span class="highlight">unlock</span> business
				<span class="highlight">opportunities.</span>
			</p>
			<p class="bold">Expert Solutions.</p>
			<p>
				Our <span class="highlight">experts design</span> strategies for measurable
				<span class="highlight">success.</span>
			</p>
			<p class="bold">Unleash Potential.</p>
			<p>
				Simple, effective, transformative—let’s <span class="highlight">elevate</span> your business
				together.
			</p>
		</div>
	</section>
	<section id="our-services">
		<div class="section-container">
			<h2>Our Services</h2>
			<p>We provide a multitude of services that can help your business gain valuable exposure.</p>
			<div class="services-list">
				<div class="card">
					<h3>Social Media Management</h3>
					<p>Strategy, execution, analytics, and reporting.</p>
				</div>
				<div class="card">
					<h3>Website Building</h3>
					<p>Custom design, development, e-commerce, and SEO.</p>
				</div>
				<div class="card">
					<h3>Content Creation</h3>
					<p>Filming, editing, graphic design, and copywriting</p>
				</div>
				<div class="card">
					<h3>Advertising</h3>
					<p>Facebook ads, flyers, and other promotional materials.</p>
				</div>
				<div class="card">
					<h3>Customer Engagement</h3>
					<p>Automated chat responses, surveys, and review management.</p>
				</div>
			</div>
		</div>
	</section>
</div>

<style lang="scss">
	.content {
		section {
			.section-container {
				max-width: calc(1200px + 2rem);
				padding: 0rem 2rem;
				margin: auto;
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

			h2 {
				@include title-md;

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
			padding-top: 2rem;
			overflow-x: clip;

			h1 {
				@include title-xl;
				font-size: 196px;

				@media screen and (max-width: 700px) {
					font-size: 128px;
				}

				@media screen and (max-width: 430px) {
					font-size: 96px;
				}
			}

			.text-infinite-scroll {
				overflow-x: clip;
				display: flex;
				width: 1000vw;

				h1 {
					animation: scroll 10s infinite linear;
					white-space: pre;

					@media (prefers-reduced-motion) {
						animation: scroll 30s infinite linear;
					}
				}

				@keyframes scroll {
					from {
						transform: translate(0);
					}

					to {
						transform: translateX(-100%);
					}
				}
			}

			.section-container {
				padding-top: 4rem;
				padding-bottom: 2rem;

				p {
					@include paragraph-lg;
					padding-bottom: 1rem;
				}

				h2 {
					@include title-md;
					padding-bottom: 1rem;

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

				.bold {
					font-weight: bold;
				}
                
				.highlight {
					color: $accent;
				}
			}
		}

		#our-services {
			.section-container {
				display: flex;
				flex-direction: column;
				gap: 2rem;
				padding: 2rem;

				.services-list {
					display: flex;
					flex-wrap: wrap;
					gap: 2rem;

					.card {
						width: min(300px, 90vw);
						aspect-ratio: 1;
						background-color: rgba(0, 0, 0, 0.4);
						backdrop-filter: blur(1rem);
						border-radius: 1rem;
						display: flex;
						flex-direction: column;
						justify-content: space-around;
						padding: 1rem;
						text-align: center;

						h3 {
							@include paragraph-lg;
						}
						 
						p {
							@include paragraph-md;
						}
					}
				}
			}

			h2 {
				@include title-xl;
				padding-bottom: 1rem;
			}

			p {
				@include paragraph-lg;
			}
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
