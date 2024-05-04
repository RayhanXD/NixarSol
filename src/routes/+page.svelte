<script lang="ts">
	// @ts-ignore 
	import LocomotiveScroll from 'locomotive-scroll';
	import { Gradient } from '$lib/Gradient';
	import { getContext, onMount } from 'svelte';
	import { type Writable } from 'svelte/store';

	let homeText: HTMLDivElement;
	let bottomText: HTMLDivElement;
	let aboutSection: HTMLElement;
	let scroll: { scrollTo: (arg0: string | HTMLElement | null) => void; on: (arg0: string, arg1: () => void) => void; };

	const scrollStore: Writable<any> = (getContext('locomotive-scroll') as any).scrollStore;

	onMount(() => {
		scroll = new LocomotiveScroll({
			el: document.querySelector('[data-scroll-container]'),
			smooth: true
		});
		scrollStore.set(scroll);

		const gradient = new Gradient();
		// @ts-ignore
		gradient.initGradient('#gradient-canvas');

		const homeElements = [homeText, bottomText];

		const updateHomeVisibility = () => {
			homeElements.forEach((e) => {
				if (aboutSection.getBoundingClientRect().top < e.getBoundingClientRect().top) {
					e.style.visibility = 'hidden';
				} else {
					e.style.visibility = 'visible';
				}
			});
		};

		updateHomeVisibility();

		scroll.on('scroll', () => updateHomeVisibility());
	});
</script>

<div class="content">
	<section id="home">
		<div class="home-container" bind:this={homeText} data-scroll data-scroll-sticky data-scroll-target="#scroll-container">
			<div bind:this={homeText}>
				<h1>Nixar Solutions</h1>
				<h2>Know your potential</h2>
			</div>
			<div class="bottom-text" bind:this={bottomText}>
				<p>Social media marketing agency<br /><span class="highlight">Know your potential.</span></p>
				<p>We help you reach the platform <span class="highlight">you deserve.</span></p>
				<a href='/' class="hover-link" on:click|preventDefault={() => scroll.scrollTo(document.getElementById('about-us'))}>
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
				A digital marketing agency adapted to the <span class="highlight">needs of the future.</span>
			</p>
			<p>
				Together, we can evaluate <span class="highlight">your needs</span> and let you know
				<span class="highlight">your potential.</span>
			</p>
			<p>
				Need exposure? We have you covered with likes, comments, and followers. <span
					class="highlight">Fast.</span>
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
			<p>
				Start your journey <a href="mailto:owennixon@nixar.com" class="highlight hover-link">here</a>
			</p>
		</div>
	</section>
	<section id="our-services">
		<div class="section-container">
			<h2>Our Services</h2>
			<p>We provide a <span class="highlight">multitude of services</span> that can help your business gain <span class="highlight">valuable exposure.</span></p>
			<div class="services-list">
				<div class="card">
					<h3>Social Media Management</h3>
					<p><span class="highlight">Strategy</span>, execution, analytics, and <span class="highlight">reporting.</span></p>
				</div>
				<div class="card">
					<h3>Website Building</h3>
					<p><span class="highlight">Custom design</span>, development, e-commerce, and <span class="highlight">search engine optimization.</span></p>
				</div>
				<div class="card">
					<h3>Content Creation</h3>
					<p><span class="highlight">Filming</span>, editing, <span class="highlight">graphic design</span>, and copywriting.</p>
				</div>
				<div class="card">
					<h3>Advertising</h3>
					<p><span class="highlight">Facebook ads</span>, flyers, and other <span class="highlight">promotional materials.</span></p>
				</div>
				<div class="card">
					<h3>Customer Engagement</h3>
					<p><span class="highlight">Automated chat responses</span>, surveys, and <span class="highlight">review management.</span></p>
				</div>
			</div>
		</div>
	</section>
	<section id="testimonials">
		<div class="section-container">
			<h1>Testimonials</h1>
			<h3>"Partnering with Nixar Marketing Company has been an absolute <span class="highlight">game-changer</span> for our tire and wheel shop, Tire and Wheel Warehouse. Owen and Anwar, the owners, have been <span class="highlight">instrumental</span> in taking our online and walk-in retail store to <span class="highlight">unprecedented levels of success</span>. Their strategic approach, combined with their <span class="highlight">dedication and expertise</span>, has propelled our business to <span class="highlight">new heights</span> that I couldn’t have dreamed of. Working with Nixar Marketing Company has truly been an awesome experience, and I highly recommend them to any business looking to <span class="highlight">revolutionize their marketing efforts</span>."</h3>
			<div class="testimonial-info">
				<img src="/tww.jpg" alt="Tire & Wheel Warehouse" />
				<p>- Tire & Wheel Warehouse U.S.A.</p>
			</div>
			<h2>2-Month Growth</h2>
			<div class="results">
				<div class="result">
					<h4>+133K</h4>
					<p>Post views</p>
				</div>
				<div class="result">
					<h4>+13K</h4>
					<p>Likes</p>
				</div>
				<div class="result">
					<h4>+114K</h4>
					<p>Unique viewers</p>
				</div>
				<div class="result">
					<h4>+13K</h4>
					<p>Followers</p>
				</div>
			</div>
			<h2>Executed Strategies</h2>
			<div class="dropdown-list-cols">
				<div class="dropdown-list">
					<div class="spacer"></div>
					<div class="dropdown">
						<h3>Content <span class="highlight">Marketing</span></h3>
						<div class="description">
							<p>
								Assisting in identifying brand ambassadors, scripting, photo and video editing,
								crafting advertisements, and creating engaging memes
							</p>
						</div>
					</div>
					<div class="spacer"></div>
					<div class="dropdown">
						<h3>Social <span class="highlight">Media</span> Marketing</h3>
						<div class="description">
							<p>
								Managing and executing social media strategies across TikTok, Instagram, Facebook,
								and YouTube. This includes content creation, scheduling posts for optimal
								engagement, researching hashtags, identifying trending audios, monitoring trends,
								and adapting to algorithm updates.
							</p>
						</div>
					</div>
					<div class="spacer"></div>
					<div class="dropdown">
						<h3>Search <span class="highlight">Engine</span> Optimization</h3>
						<div class="description">
							<p>
								Creating keyword-rich content through blogs and customer testimonials, while
								strategically utilizing photos and videos to enhance engagement and visibility.
							</p>
						</div>
					</div>
					<div class="spacer"></div>
				</div>
				<div class="dropdown-list">
					<div class="spacer"></div>
					<div class="dropdown">
						<h3>Pay <span class="highlight">Per</span> Click</h3>
						<div class="description">
							<p>
								Assisting in identifying brand ambassadors, scripting, photo and video editing,
								crafting advertisements, and creating engaging memes
							</p>
						</div>
					</div>
					<div class="spacer"></div>
					<div class="dropdown">
						<h3>News <span class="highlight">Jacking</span></h3>
						<div class="description">
							<p>
								Capitalizing on trending news by creating unique twists that highlight our client's
								offerings. For example, find all the wheels and tires featured in the latest 'Fast
								and Furious' movie exclusively at Tire Wheel Warehouse.
							</p>
						</div>
					</div>
					<div class="spacer"></div>
				</div>
			</div>
		</div>
	</section>
	<section id="faq">
		<div class="section-container">
			<h1>FAQs</h1>
			<h3>Have questions? Check out the frequently asked questions below or <a href="/" class="hover-link" on:click|preventDefault={() => scroll.scrollTo(document.getElementById('contact-us'))}>contact us.</a></h3>
			<div class="dropdown-list">
				<div class="spacer"></div>
				<div class="dropdown">
					<h3>What <span class="highlight">digital marketing services </span>does NIXAR Solutions offer?</h3>
					<div class="description">
						<p>
							NIXAR Solutions offers a comprehensive range of digital marketing services including social media management, content creation, SEO optimization, pay-per-click advertising, and email marketing, tailored to boost your brand's online presence and engagement.
						</p>
					</div>
				</div>
				<div class="spacer"></div>
				<div class="dropdown">
					<h3>Can you explain the <span class="highlight">different pricing</span> models available at NIXAR Solutions?</h3>
					<div class="description">
						<p>
							We offer flexible pricing models to suit various business needs and budgets, including project-based pricing, retainer models for ongoing services, and performance-based pricing that depends on achieving specific results.
						</p>
					</div>
				</div>
				<div class="spacer"></div>
				<div class="dropdown">
					<h3>What <span class="highlight">service packages </span>does NIXAR Solutions provide, and are they <span class="highlight">customizable</span>?</h3>
					<div class="description">
						<p>
							Our service packages range from basic digital marketing setups for startups to advanced strategies for large enterprises. Each package can be customized to include additional services such as video marketing and advanced analytics as per your business requirements.
						</p>
					</div>
				</div>
				<div class="spacer"></div>
				<div class="dropdown">
					<h3>How can I <span class="highlight">get started</span> with digital marketing services at NIXAR Solutions?</h3>
					<div class="description">
						<p>
							Getting started is simple! Just contact us through our website or give us a call. We'll set up an initial consultation to discuss your needs, objectives, and how our services can be tailored to achieve your goals.
						</p>
					</div>
				</div>
				<div class="spacer"></div>
				<div class="dropdown">
					<h3>Are there any <span class="highlight">specific industries</span> or business sizes that NIXAR Solutions <span class="highlight">specializes</span> in?</h3>
					<div class="description">
						<p>
							While NIXAR Solutions has expertise across a variety of industries, we specialize in serving small to medium-sized businesses in sectors such as retail, technology, and healthcare, helping them to maximize their digital marketing efforts.
						</p>
					</div>
				</div>
				<div class="spacer"></div>
				<div class="dropdown">
					<h3>What makes NIXAR Solutions <span class="highlight">stand out</span> in the digital marketing <span class="highlight">industry</span>?</h3>
					<div class="description">
						<p>
							Our commitment to personalized service, our focus on delivering measurable results, and our ability to stay ahead of digital marketing trends set us apart. We pride ourselves on being not just service providers, but strategic partners to our clients.
						</p>
					</div>
				</div>
				<div class="spacer"></div>
				<div class="dropdown">
					<h3>How does NIXAR Solutions <span class="highlight">ensure the effectiveness</span> of its digital marketing <span class="highlight">strategies</span>?</h3>
					<div class="description">
						<p>
							We use a data-driven approach to monitor and analyze the performance of all campaigns, allowing us to adjust strategies in real time for optimal effectiveness. Regular reports and updates are provided to ensure transparency and alignment with client goals.
						</p>
					</div>
				</div>
				<div class="spacer"></div>
				<div class="dropdown">
					<h3>What are the <span class="highlight">steps involved</span> in beginning a project with NIXAR Solutions?</h3>
					<div class="description">
						<p>
							To start a project, we conduct a detailed analysis of your current marketing efforts, discuss your business objectives, and develop a tailored strategy. Once approved, we move into implementation, with ongoing monitoring and optimization.
						</p>
					</div>
				</div>
				<div class="spacer"></div>
				<div class="dropdown">
					<h3>Does NIXAR Solutions offer any <span class="highlight">ongoing support</span> or maintenance <span class="highlight">services</span> post project completion?</h3>
					<div class="description">
						<p>
							Yes, we provide ongoing support and maintenance services to ensure that your marketing efforts continue to be effective. This includes regular updates, optimizations, and consultations as needed.
						</p>
					</div>
				</div>
				<div class="spacer"></div>
				<div class="dropdown">
					<h3>How does NIXAR Solutions stay <span class="highlight">updated</span> with the <span class="highlight">latest digital marketing trends</span> and technologies?</h3>
					<div class="description">
						<p>
							Our team regularly participates in industry workshops and conferences, and we invest in continuous training and certification. This commitment to professional development allows us to implement the latest strategies and technologies for our clients.
						</p>
					</div>
				</div>
				<div class="spacer"></div>
			</div>
		</div>
	</section>
	<section id="contact-us">
		<div class="section-container">
			<h1>Contact Us</h1>
			<div class="dropdown-list">
				<div class="spacer"></div>
				<a href="mailto:anwarmirza@nixar.com">
					<h3><span>Inquiries</span><span class="highlight">anwarmirza@nixar.com<br>owennixon@nixar.com</span></h3>
				</a>
				<div class="spacer"></div>
				<a href="tel:972-469-2699">
					<h3><span>Call Us</span><span class="highlight">972-469-2699<br>214-885-3366</span></h3>
				</a>
				<div class="spacer"></div>
				<a href="https://instagram.com/nixarsolutions">
					<h3><span>Instagram</span><span class="highlight">@nixarsolutions</span></h3>
				</a>
				<div class="spacer"></div>
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

	:global(.highlight) {
		color: $accent;
		
		&::after {
			background-color: $accent;
		}
	}

	.dropdown-list-cols {
		display: grid;
		grid-template-columns: 1fr 1fr;
		gap: 4rem;

		@media screen and (max-width: 800px) {
			display: flex;
			flex-direction: column;
			justify-content: start;
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
				@include title-xs;
				font-size: 24px !important;
				padding: 0.5rem 0 !important;
				padding-top: 12px !important;
				text-align: left !important;
			}

			.description {
				display: grid;
				grid-template-rows: 0fr;
				transition: grid-template-rows 0.7s ease;
				overflow-y: hidden;

				p {
					@include paragraph-md;
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
				height: 100svh;
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
				line-height: 102%;

				@media screen and (max-width: 867px) {
					transform: translateY(-10%);
				}

				@media screen and (max-width: 585px) {
					transform: translateY(-20%);
					font-size: 48px;
				}

				@media screen and (max-width: 430px) {
					font-size: 32px;
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
			}
		}

		#our-services {
			.section-container {
				display: flex;
				flex-direction: column;
				gap: 2rem;
				padding: 3rem 2rem;
				padding-bottom: 0;

				.services-list {
					display: flex;
					flex-wrap: wrap;
					justify-content: center;
					gap: 2rem;
					margin-bottom: 4rem;

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
				padding: 3rem 2rem;

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

				.results {
					display: flex;
					justify-content: space-between;
					gap: 4rem;
					padding-bottom: 4rem;
					flex-wrap: wrap;

					.result {
						display: flex;
						flex-direction: column;

						h4 {
							@include title-xl;
							font-size: 72px;
							font-weight: 600;
							color: $accent;
						}

						p {
							font-size: 28px;
						}
					}
				}

				h3 {
					@include title-xs;
					padding: 1rem 0;
					text-align: center;
				}

				.testimonial-info {
					margin: 2rem 0;
					padding-bottom: 2rem;
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
					min-height: 340px;

					@media screen and (max-width: 800px) {
						min-height: 0;
					}
				}
			}
		}

		#faq {
			.section-container {
				padding: 3rem 2rem;

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

				h3 {
					@include title-xs;
					padding-top: 1rem;
					padding-bottom: 2rem;
					text-align: left;
				}
				
			}
		}

		#contact-us {
			background: black;
			min-height: 100svh;
			isolation: isolate;

			.section-container {
				h1 {
					@include title-xl;
					padding: 3rem 0 3rem 0;

					@media screen and (max-width: 600px) {
						font-size: 96px;
					}

					@media screen and (max-width: 450px) {
						font-size: 64px;
					}
				}

				.dropdown-list:hover {
					a {
						opacity: 0.4;
					}
				}

				a {
					width: 100%;
					color: white;
					text-decoration: none;
					transition: opacity 300ms ease;

					h3 {
						@include title-md;
						width: 100%;
						display: flex;
						flex-wrap: wrap;
						justify-content: space-between;
						padding: 0.5rem 0;
						column-gap: 1rem;

						@media screen and (max-width: 550px) {
							font-size: 32px;
						}

						@media screen and (max-width: 380px) {
							font-size: 24px;
						}

						.highlight {
							text-align: right;
							flex: 2;
						}
					}

					&:hover {
						opacity: 1 !important;
					}
				}
			}
		}
	}
</style>
