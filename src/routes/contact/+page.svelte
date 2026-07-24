<script lang="ts">
	import siteData from '$lib/data/site.json';
</script>

<svelte:head>
	<title>{siteData.seo.contact.title}</title>
	<meta name="description" content={siteData.seo.contact.description} />
	<meta name="keywords" content={siteData.seo.contact.keywords} />
	<meta property="og:title" content={siteData.seo.contact.title} />
	<meta property="og:description" content={siteData.seo.contact.description} />
	<meta property="og:type" content="website" />
</svelte:head>

<section class="contact-page">
	<div class="contact-inner">
		<div class="contact-intro">
			<p class="eyebrow">Get in touch</p>
			<h1 class="page-title">Let's<br /><em>Connect</em></h1>
			<p class="contact-subtitle">
				Looking for a creative leader who blends strategy with execution?
			</p>
		</div>

		<div class="contact-links">
			<a href="mailto:{siteData.contact.email}" class="contact-item">
				<div class="contact-accent" style="background-color: var(--color-pink)"></div>
				<i class="fa-regular fa-envelope contact-icon"></i>
				<div class="contact-text">
					<span class="contact-label">Email</span>
					<span class="contact-value">{siteData.contact.email}</span>
				</div>
				<span class="contact-arrow">→</span>
			</a>

			<a
				href={siteData.contact.linkedin}
				target="_blank"
				rel="noopener noreferrer"
				class="contact-item"
			>
				<div class="contact-accent" style="background-color: var(--color-blue)"></div>
				<i class="fa-brands fa-linkedin-in contact-icon"></i>
				<div class="contact-text">
					<span class="contact-label">LinkedIn</span>
					<span class="contact-value">tara-devi</span>
				</div>
				<span class="contact-arrow">→</span>
			</a>
		</div>
	</div>
</section>

<style>
	.contact-page {
		padding: clamp(3rem, 7vh, 6rem) var(--page-pad);
		min-height: calc(100svh - 4.5rem);
		display: flex;
		align-items: center;
		background:
			radial-gradient(circle at 78% 24%, rgba(229, 223, 235, 0.95), transparent 30rem),
			radial-gradient(circle at 18% 82%, rgba(220, 229, 231, 0.7), transparent 25rem);
	}

	.contact-inner {
		max-width: var(--page-max);
		margin: 0 auto;
		width: 100%;
		display: grid;
		grid-template-columns: minmax(0, 1.05fr) minmax(360px, 0.75fr);
		gap: clamp(4rem, 10vw, 10rem);
		align-items: end;
	}

	.contact-intro {
		display: flex;
		flex-direction: column;
		align-items: flex-start;
	}

	.eyebrow {
		font-family: var(--font-body);
		font-size: 0.65rem;
		letter-spacing: 0.4em;
		text-transform: uppercase;
		color: var(--color-muted);
		margin-bottom: 1rem;
		font-weight: 400;
	}

	.page-title {
		font-family: var(--font-display);
		font-size: clamp(5rem, min(11vw, 17vh), 10rem);
		font-weight: 300;
		line-height: 0.88;
		letter-spacing: -0.055em;
		margin-bottom: clamp(2rem, 5vh, 3.5rem);
	}

	.page-title em {
		font-style: italic;
		font-weight: 300;
	}

	.contact-subtitle {
		font-family: var(--font-display);
		font-size: clamp(1.1rem, 1.8vw, 1.45rem);
		font-style: italic;
		font-weight: 300;
		color: var(--color-muted);
		margin-bottom: 0;
		line-height: 1.55;
		letter-spacing: 0.01em;
		max-width: 510px;
	}

	.contact-links {
		display: flex;
		flex-direction: column;
		border-top: 1px solid var(--color-border);
		border-bottom: 1px solid var(--color-border);
	}

	.contact-item {
		display: flex;
		align-items: center;
		gap: 1.5rem;
		padding: clamp(1.5rem, 3.5vh, 2.5rem) 0;
		border-bottom: 1px solid var(--color-border);
		transition: transform 0.25s cubic-bezier(0.25, 0.46, 0.45, 0.94);
	}

	.contact-item:first-child {
		border-top: 0;
	}

	.contact-item:hover {
		transform: translateX(8px);
	}

	.contact-accent {
		width: 0.65rem;
		height: 3.5rem;
		flex-shrink: 0;
		border-radius: 1px;
	}

	.contact-icon {
		font-size: 1.1rem;
		width: 1.25rem;
		text-align: center;
		color: var(--color-muted);
		flex-shrink: 0;
	}

	.contact-text {
		display: flex;
		flex-direction: column;
		gap: 0.15rem;
		flex: 1;
	}

	.contact-label {
		font-family: var(--font-body);
		font-size: 0.62rem;
		letter-spacing: 0.25em;
		text-transform: uppercase;
		color: var(--color-muted);
		font-weight: 400;
	}

	.contact-value {
		font-family: var(--font-display);
		font-size: clamp(1.25rem, 2vw, 1.7rem);
		font-weight: 300;
		letter-spacing: 0.02em;
	}

	.contact-arrow {
		font-size: 1.1rem;
		color: var(--color-muted);
		transition: transform 0.25s ease, color 0.25s ease;
	}

	.contact-item:hover .contact-arrow {
		transform: translateX(4px);
		color: var(--color-text);
	}

	@media (max-width: 900px) {
		.contact-page {
			min-height: auto;
		}

		.contact-inner {
			grid-template-columns: 1fr;
			gap: 3.5rem;
			align-items: start;
		}
	}

	@media (max-width: 640px) {
		.contact-page {
			padding: 3rem var(--page-pad);
			align-items: flex-start;
		}

		.page-title {
			font-size: clamp(4.25rem, 24vw, 7rem);
			line-height: 0.92;
		}

		.contact-item {
			gap: 1rem;
		}

		.contact-value {
			font-size: 1.15rem;
			overflow-wrap: anywhere;
		}
	}
</style>
