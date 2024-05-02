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

		updateHomeVisibility();

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
				<a href='#about-us' class='hover-link'>
					<p>[SCROLL]</p>
				</a>	
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
					<p>Filming, editing, graphic design, and copywriting.</p>
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
	<section id="testimonials">
		<div class="section-container">
			<h1>Testimonials</h1>
			<h3>Insert testimonial here</h3>
			<div class="testimonial-info">
				<img src="/tww.jpg" alt='Tire & Wheel Warehouse' />
				<p>Tire & Wheel Warehouse U.S.A. </p>
			</div>
			<h2>Executed Strategies</h2>
			<div class="dropdown-list-cols">

				<div class="dropdown-list">
					<div class="spacer"></div>
					<div class="dropdown">
						<h3>Content Marketing</h3>
						<div class="description">
							<p>Assisting in identifying brand ambassadors, scripting, photo and video editing, crafting advertisements, and creating engaging memes</p>
						</div>
					</div>
					<div class="spacer"></div>
					<div class="dropdown">
						<h3>Social Media Marketing</h3>
						<div class="description">
							<p>Managing and executing social media strategies across TikTok, Instagram, Facebook, and YouTube. This includes content creation, scheduling posts for optimal engagement, researching hashtags, identifying trending audios, monitoring trends, and adapting to algorithm updates.</p>
						</div>
					</div>
					<div class="spacer"></div>
					<div class="dropdown">
						<h3>Search Engine Optimization</h3>
						<div class="description">
							<p>Creating keyword-rich content through blogs and customer testimonials, while strategically utilizing photos and videos to enhance engagement and visibility.</p>
						</div>
					</div>
					<div class="spacer"></div>
				</div>
				<div class="dropdown-list">
					<div class="spacer"></div>
					<div class="dropdown">
						<h3>Pay Per Click</h3>
						<div class="description">
							<p>Assisting in identifying brand ambassadors, scripting, photo and video editing, crafting advertisements, and creating engaging memes</p>
						</div>
					</div>
					<div class="spacer"></div>
					<div class="dropdown">
						<h3>News Jacking</h3>
						<div class="description">
							<p>Capitalizing on trending news by creating unique twists that highlight our client's offerings. For example, find all the wheels and tires featured in the latest 'Fast and Furious' movie exclusively at Tire Wheel Warehouse.</p>
						</div>
					</div>
					<div class="spacer"></div>
				</div>
			</div>
		</div>
	</section>
</div>

<style lang="scss">
	:global(.hover-link) {
		color: white;
		text-decoration: none;
		position: relative;

		&::after {
			content: '';
			position: absolute;
			top: 100%;
			left: 0;
			right: 100%;
			background-color: white;
			height: 1px;
			transition: right 600ms cubic-bezier(0.22, 1, 0.36, 1);
		}

		&:hover::after {
			right: 0;
		}
	}

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
				padding: 3rem 2rem;

				.services-list {
					display: flex;
					flex-wrap: wrap;
					justify-content: center;
					gap: 2rem;

					.card {
						width: auto;
						max-width: 300px;
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

				@media screen and (max-width: 600px) {
					font-size: 96px;
				}

				@media screen and (max-width: 450px) {
					font-size: 64px;
				}
			}

			p {
				@include paragraph-lg;
			}
		}

		#testimonials {
			.section-container {
				padding-bottom: 3rem;

				h1 {
					@include title-xl;
					padding-bottom: 1rem;
					

					@media screen and (max-width: 600px) {
						font-size: 96px;
					}

					@media screen and (max-width: 450px) {
						font-size: 64px;
					}
				}
				
				h2 {
					@include title-md;
					padding-bottom: 1rem;
				}

				h3 {
					@include title-md;
					padding: 1rem 0;
					text-align: center;
				}

				.testimonial-info {
					margin: 2rem 0;
					display: flex;
					flex-direction: column;
					gap: 1rem;
					align-items: center;
					
					img {
						border-radius: 50%;
						width: 100px;
						height: 100px;
					}

					p {
						text-align: center;
					}
				}

				.dropdown-list-cols {
					display: grid;
					grid-template-columns: 1fr 1fr;
					gap: 4rem;
					min-height: 300px;

					@media screen and (max-width: 800px) {
						flex-direction: column;
						gap: 0;
					}
				}

				.dropdown-list {
					display: flex;
					flex-direction: column;
					align-items: flex-start;

					.spacer {
						height: 1px;
						width: 100%;
						background-color: white;
					}

					.dropdown {
						display: flex;
						flex-direction: column;

						h3 {
							font-size: 24px;
							padding: 0.5rem 0;
							text-align: left;
						}

						.description {
							display: grid;
							grid-template-rows: 0fr;
							transition: grid-template-rows .7s ease;
							overflow-y: hidden;

							p {
								min-height: 0;
								padding-bottom: 4px;
							}
						}

						&:hover {
							.description {
								grid-template-rows: 1fr;
							}
						}
					}
				}
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
