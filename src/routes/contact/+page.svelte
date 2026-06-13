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
		<div class="contact-grid">

			<!-- Left: Editorial headline -->
			<div class="contact-left">
				<p class="eyebrow">Contact</p>
				<h1 class="headline">
					<span>Let's</span>
					<em>work</em>
					<span>together.</span>
				</h1>
				<p class="tagline">
					Open to art direction, campaign production, and creative strategy engagements.
				</p>
			</div>

			<!-- Right: Links -->
			<div class="contact-right">
				<p class="contact-prompt">Reach out directly</p>
				<div class="contact-links">
					<a href="mailto:{siteData.contact.email}" class="contact-item">
						<div class="contact-item-inner">
							<div class="contact-meta">
								<span class="contact-label">Email</span>
								<span class="contact-value">{siteData.contact.email}</span>
							</div>
							<span class="contact-arrow">→</span>
						</div>
					</a>

					<a
						href={siteData.contact.linkedin}
						target="_blank"
						rel="noopener noreferrer"
						class="contact-item"
					>
						<div class="contact-item-inner">
							<div class="contact-meta">
								<span class="contact-label">LinkedIn</span>
								<span class="contact-value">tara-devi</span>
							</div>
							<span class="contact-arrow">→</span>
						</div>
					</a>
				</div>
			</div>

		</div>
	</div>
</section>

<style>
	.contact-page {
		min-height: calc(100svh - 4rem);
		display: flex;
		align-items: center;
		padding: 5rem var(--page-pad);
	}

	.contact-inner {
		max-width: var(--page-max);
		margin: 0 auto;
		width: 100%;
	}

	.contact-grid {
		display: grid;
		grid-template-columns: 1.1fr 0.9fr;
		gap: 8rem;
		align-items: center;
	}

	/* Left */
	.contact-left {
		display: flex;
		flex-direction: column;
		gap: 2.5rem;
	}

	.eyebrow {
		font-family: var(--font-body);
		font-size: 0.65rem;
		letter-spacing: 0.4em;
		text-transform: uppercase;
		color: var(--color-muted);
		font-weight: 400;
	}

	.headline {
		font-family: var(--font-display);
		font-size: clamp(3.5rem, 7vw, 6.5rem);
		font-weight: 300;
		line-height: 1;
		letter-spacing: -0.02em;
		display: flex;
		flex-direction: column;
	}

	.headline em {
		font-style: italic;
		font-weight: 300;
		color: var(--color-muted);
	}

	.tagline {
		font-family: var(--font-display);
		font-size: 1rem;
		font-style: italic;
		font-weight: 300;
		color: var(--color-muted);
		line-height: 1.8;
		letter-spacing: 0.01em;
		max-width: 36ch;
		padding-left: 1.25rem;
		border-left: 1px solid var(--color-border);
	}

	/* Right */
	.contact-right {
		display: flex;
		flex-direction: column;
		gap: 1.75rem;
	}

	.contact-prompt {
		font-family: var(--font-body);
		font-size: 0.65rem;
		letter-spacing: 0.4em;
		text-transform: uppercase;
		color: var(--color-muted);
		font-weight: 400;
	}

	.contact-links {
		display: flex;
		flex-direction: column;
	}

	.contact-item {
		display: block;
		padding: 1.75rem 0;
		border-bottom: 1px solid var(--color-border);
		text-decoration: none;
		color: inherit;
	}

	.contact-item:first-child {
		border-top: 1px solid var(--color-border);
	}

	.contact-item-inner {
		display: flex;
		justify-content: space-between;
		align-items: center;
		gap: 1rem;
		transition: transform 0.3s cubic-bezier(0.25, 0.46, 0.45, 0.94);
	}

	.contact-item:hover .contact-item-inner {
		transform: translateX(6px);
	}

	.contact-meta {
		display: flex;
		flex-direction: column;
		gap: 0.3rem;
	}

	.contact-label {
		font-family: var(--font-body);
		font-size: 0.58rem;
		letter-spacing: 0.3em;
		text-transform: uppercase;
		color: var(--color-muted);
		font-weight: 400;
	}

	.contact-value {
		font-family: var(--font-display);
		font-size: clamp(1.2rem, 2.2vw, 1.6rem);
		font-weight: 300;
		letter-spacing: -0.01em;
		color: var(--color-text);
	}

	.contact-arrow {
		font-size: 1.25rem;
		color: var(--color-muted);
		flex-shrink: 0;
		transition: transform 0.25s ease, color 0.25s ease;
	}

	.contact-item:hover .contact-arrow {
		transform: translateX(4px);
		color: var(--color-text);
	}

	@media (max-width: 900px) {
		.contact-grid {
			grid-template-columns: 1fr;
			gap: 4rem;
		}

		.contact-page {
			align-items: flex-start;
		}
	}

	@media (max-width: 640px) {
		.contact-page {
			padding: 3rem var(--page-pad);
			min-height: unset;
		}
	}
</style>
