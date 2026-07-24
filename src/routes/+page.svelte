<script lang="ts">
	import siteData from '$lib/data/site.json';
	import projectsData from '$lib/data/projects.json';

	const featuredProjects = projectsData.filter((p) => p.isFeatured);
</script>

<svelte:head>
	<title>{siteData.seo.home.title}</title>
	<meta name="description" content={siteData.seo.home.description} />
	<meta name="keywords" content={siteData.seo.home.keywords} />
	<meta property="og:title" content={siteData.seo.home.title} />
	<meta property="og:description" content={siteData.seo.home.description} />
	<meta property="og:type" content="website" />
	<meta property="og:url" content="https://taradevi.studio/" />
	<meta property="og:image" content="https://taradevi.studio{featuredProjects[0].image}" />
	<meta name="twitter:title" content={siteData.seo.home.title} />
	<meta name="twitter:description" content={siteData.seo.home.description} />
	<meta name="twitter:image" content="https://taradevi.studio{featuredProjects[0].image}" />
	<link rel="canonical" href="https://taradevi.studio/" />
</svelte:head>

<!-- Hero Section -->
<section class="hero">
	<div class="hero-inner">
		<p class="hero-eyebrow">Creative Strategy · Visual Production · Brand Storytelling</p>
		<h1 class="hero-title">{siteData.title}</h1>
		<p class="hero-dash">—</p>
		<p class="hero-summary">{siteData.summary}</p>
	</div>
</section>

<!-- Featured Projects -->
<section class="projects">
	<div class="divider"></div>
	<div class="projects-header">
		<h2 class="section-heading">Selected Work</h2>
	</div>
	<div class="projects-list">
		{#each featuredProjects as project, i}
			<a href="/work/{project.slug}" class="project-card-link">
				<article class="project-card" style="--accent: {project.color}">
					<div class="project-card-inner">
						<div class="project-image">
							<img src={project.image} alt={project.title} loading="lazy" />
						</div>
						<div class="project-details">
							<h3 class="project-title">{project.title}</h3>
							<p class="project-note">{project.note}</p>
							<div class="project-tags">
								{#each project.tags as tag}
									<span class="tag">{tag}</span>
								{/each}
							</div>
							<span class="project-link">
								View Project <span class="arrow">→</span>
							</span>
						</div>
					</div>
				</article>
			</a>
		{/each}
	</div>
	<div class="view-all-wrapper">
		<div class="view-all">
			<a href="/work">View all work →</a>
		</div>
	</div>
</section>

<style>
	/* Hero */
	.hero {
		padding: 0 var(--page-pad);
		display: flex;
		flex-direction: column;
		align-items: center;
		justify-content: center;
		min-height: min(820px, calc(100svh - 4.5rem));
		position: relative;
		text-align: center;
		background:
			radial-gradient(circle at 12% 22%, rgba(234, 219, 213, 0.7), transparent 24rem),
			radial-gradient(circle at 88% 78%, rgba(220, 229, 231, 0.55), transparent 25rem);
	}

	.hero-inner {
		max-width: 1120px;
		text-align: center;
		display: flex;
		flex-direction: column;
		align-items: center;
	}

	.hero-eyebrow {
		font-family: var(--font-body);
		font-size: 0.7rem;
		letter-spacing: 0.38em;
		text-transform: uppercase;
		color: var(--color-muted);
		font-weight: 400;
		margin-bottom: clamp(2rem, 6vh, 4.5rem);
	}

	.hero-title {
		font-family: var(--font-display);
		font-size: clamp(3.4rem, 9vw, 8.2rem);
		font-weight: 300;
		line-height: 1.12;
		color: var(--color-text);
		letter-spacing: -0.055em;
		margin-bottom: 0;
	}

	.hero-dash {
		font-family: var(--font-display);
		font-size: 1.2rem;
		font-weight: 300;
		color: var(--color-muted);
		letter-spacing: 0.5em;
	}

	.hero-summary {
		font-family: var(--font-display);
		font-size: clamp(1rem, 1.7vw, 1.3rem);
		font-weight: 300;
		font-style: italic;
		line-height: 1.75;
		color: var(--color-muted);
		letter-spacing: 0.01em;
		max-width: 860px;
	}

	.divider {
		max-width: var(--page-max);
		margin: 0 auto 5rem;
		padding: 0 var(--page-pad);
		border-top: 1px solid var(--color-border);
	}

	.project-card-link {
		display: block;
		text-decoration: none;
		color: inherit;
	}

	/* Projects */
	.projects {
		padding-top: 2rem;
		padding-bottom: 5rem;
		background: linear-gradient(180deg, transparent, rgba(250, 248, 243, 0.72) 14rem);
	}

	.projects-header {
		max-width: var(--page-max);
		margin: 0 auto;
		padding: 0 var(--page-pad);
	}

	.projects-list {
		display: flex;
		flex-direction: column;
		gap: 1px;
		margin-bottom: 2rem;
	}

	.section-heading {
		font-family: var(--font-body);
		font-size: 0.68rem;
		font-weight: 400;
		letter-spacing: 0.35em;
		text-transform: uppercase;
		color: var(--color-muted);
		margin-bottom: 3.5rem;
	}

	.project-card {
		background: var(--color-surface);
		border-top: 1px solid var(--color-border);
	}

	.project-card-inner {
		max-width: var(--page-max);
		margin: 0 auto;
		padding: clamp(2rem, 5vw, 5rem) var(--page-pad);
		display: grid;
		grid-template-columns: minmax(0, 1.45fr) minmax(280px, .55fr);
		gap: clamp(2rem, 7vw, 7rem);
		align-items: center;
	}

	.project-card-link:hover .project-card {
		background: var(--accent);
	}

	.project-card-link:nth-child(even) .project-image {
		order: 2;
	}
	.project-card-link:nth-child(even) .project-card-inner {
		grid-template-columns: minmax(280px, .55fr) minmax(0, 1.45fr);
	}

	.view-all-wrapper {
		max-width: var(--page-max);
		margin: 0 auto;
		padding: 0 var(--page-pad);
	}

	.project-image {
		border-radius: 0;
		overflow: hidden;
		aspect-ratio: 16/10;
		background-color: rgba(0, 0, 0, 0.04);
	}

	.project-image img {
		width: 100%;
		height: 100%;
		object-fit: cover;
		transition: transform 0.9s var(--ease-editorial);
	}

	.project-card-link:hover .project-image img {
		transform: scale(1.025);
	}

	.project-details {
		display: flex;
		flex-direction: column;
		gap: 0.65rem;
	}

	.project-title {
		font-family: var(--font-display);
		font-size: clamp(2rem, 3.6vw, 3.75rem);
		font-weight: 300;
		line-height: 0.98;
		margin-top: 0.3rem;
		letter-spacing: -0.01em;
	}

	.project-note {
		font-family: var(--font-body);
		font-size: 0.85rem;
		color: #504e48;
		line-height: 1.75;
		letter-spacing: 0.01em;
	}

	.project-tags {
		display: flex;
		flex-wrap: wrap;
		gap: 0.4rem;
		margin-top: 0.25rem;
	}

	.tag {
		font-family: var(--font-body);
		font-size: 0.62rem;
		padding: 0.2rem 0.6rem;
		border-radius: 0;
		background-color: transparent;
		border: 1px solid rgba(0, 0, 0, 0.18);
		letter-spacing: 0.08em;
		text-transform: uppercase;
	}

	.project-link {
		margin-top: 0.75rem;
		font-family: var(--font-body);
		font-size: 0.75rem;
		font-weight: 400;
		letter-spacing: 0.2em;
		text-transform: uppercase;
		color: var(--color-text);
		display: inline-flex;
		align-items: center;
		gap: 0.5rem;
		transition: gap 0.25s ease;
	}

	.project-link:hover {
		gap: 0.75rem;
	}

	.arrow {
		transition: transform 0.2s ease;
	}

	.project-link:hover .arrow {
		transform: translateX(4px);
	}

	.view-all {
		margin-top: 1rem;
		text-align: right;
	}

	.view-all a {
		font-family: var(--font-body);
		font-size: 0.72rem;
		font-weight: 400;
		letter-spacing: 0.25em;
		text-transform: uppercase;
		color: var(--color-muted);
		transition: color 0.3s;
	}

	.view-all a:hover {
		color: var(--color-text);
	}

	@media (max-width: 768px) {
		.hero {
			min-height: calc(100svh - 3.5rem);
			padding: 4rem var(--page-pad);
		}

		.hero-eyebrow {
			margin-bottom: 2.5rem;
		}

		.hero-dash {
			margin: 1.5rem 0;
		}

		.projects {
			padding-top: 3rem;
			padding-bottom: 3rem;
		}

		.project-card-inner {
			grid-template-columns: 1fr;
			gap: 1.5rem;
			padding: 1.75rem var(--page-pad);
		}
		.project-card-link:nth-child(even) .project-card-inner {
			grid-template-columns: 1fr;
		}
		.project-card-link:nth-child(even) .project-image {
			order: 0;
		}
	}
</style>
