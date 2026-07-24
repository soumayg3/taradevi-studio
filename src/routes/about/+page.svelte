<script lang="ts">
  import siteData from '$lib/data/site.json';

  const roles = siteData.aboutTitle.split(' | ');
  const expColors = ['var(--color-pink)', 'var(--color-yellow)'];
</script>

<svelte:head>
  <title>{siteData.seo.about.title}</title>
  <meta name="description" content={siteData.seo.about.description} />
  <meta name="keywords" content={siteData.seo.about.keywords} />
  <meta property="og:title" content={siteData.seo.about.title} />
  <meta property="og:description" content={siteData.seo.about.description} />
  <meta property="og:type" content="profile" />
</svelte:head>

<!-- Section 1: Profile -->
<section class="section profile-section">
  <div class="container">
    <div class="profile-grid">
      <div class="profile-image-col">
        <div class="profile-image-wrapper">
          <img src={siteData.profileImage} alt={siteData.name} class="profile-image" />
        </div>
      </div>
      <div class="profile-content">
        <p class="eyebrow">About</p>
        <h1 class="about-name">{siteData.name}</h1>
        <div class="about-roles">
          {#each roles as role}
            <span class="about-role">{role}</span>
          {/each}
        </div>
        <p class="about-summary">{siteData.aboutMe}</p>
        <div class="highlights">
          {#each siteData.highlights as highlight, i}
            {@const colors = ['var(--color-pink)', 'var(--color-yellow)', 'var(--color-blue)']}
            <div class="highlight-card" style="background-color: {colors[i % colors.length]}">
              <span class="highlight-value">{highlight.value}</span>
              <span class="highlight-label">{highlight.label}</span>
            </div>
          {/each}
        </div>
      </div>
    </div>
  </div>
</section>

<!-- Section 2: Expertise -->
<section class="section expertise-section">
  <div class="container">
    <p class="eyebrow">Expertise</p>
    <div class="expertise-grid">
      {#each siteData.expertise as area, i}
        {@const colors = ['var(--color-pink)', 'var(--color-yellow)', 'var(--color-blue)', 'var(--color-lavender)']}
        <div class="expertise-card" style="background-color: {colors[i % colors.length]}">
          <span class="expertise-icon">{area.icon}</span>
          <h3 class="expertise-title">{area.title}</h3>
          <p class="expertise-desc">{area.description}</p>
          <div class="skill-list">
            {#each area.skills as skill}
              <span class="skill-tag">{skill}</span>
            {/each}
          </div>
        </div>
      {/each}
    </div>
  </div>
</section>

<!-- Section 3: Experience -->
<section class="section experience-section">
  <div class="container">
    <p class="eyebrow">Experience</p>
    <div class="experience-list">
      {#each siteData.experience as job, i}
        <div class="job" style="background-color: {expColors[i % expColors.length]}">
          <div class="job-header">
            <strong class="job-company">{job.company}</strong>
            <span class="job-period">{job.period}</span>
          </div>
          <span class="job-role">{job.role}</span>
          <span class="job-location">{job.location}</span>
          <p class="job-description">{job.description}</p>
          <div class="skill-list">
            {#each job.skills as skill}
              <span class="skill-tag">{skill}</span>
            {/each}
          </div>
        </div>
      {/each}
    </div>
  </div>
</section>

<style>
  .section {
    padding: clamp(5rem, 9vw, 9rem) var(--page-pad);
  }

  .profile-section {
    min-height: calc(100svh - 4.5rem);
    padding-top: clamp(2.5rem, 5vh, 4rem);
    padding-bottom: clamp(2.5rem, 5vh, 4rem);
    display: flex;
    align-items: center;
    background:
      radial-gradient(circle at 7% 18%, rgba(234, 219, 213, 0.88), transparent 30rem),
      linear-gradient(180deg, rgba(250, 248, 243, 0.55), transparent);
  }

  .profile-section .container {
    width: 100%;
  }

  .expertise-section {
    background: linear-gradient(180deg, transparent, rgba(233, 225, 205, 0.3), transparent);
  }

  .experience-section {
    background: linear-gradient(180deg, transparent, rgba(229, 223, 235, 0.32));
  }

  .section + .section {
    padding-top: clamp(5rem, 9vw, 9rem);
  }

  .container {
    max-width: var(--page-max);
    margin: 0 auto;
  }

  .eyebrow {
    font-family: var(--font-body);
    font-size: 0.65rem;
    letter-spacing: 0.4em;
    text-transform: uppercase;
    color: var(--color-muted);
    margin-bottom: 2.5rem;
    font-weight: 400;
  }

  /* ── Section 1: Profile ── */
  .profile-grid {
    display: grid;
    grid-template-columns: minmax(320px, 0.82fr) minmax(0, 1.18fr);
    gap: clamp(3rem, 8vw, 8rem);
    align-items: center;
  }

  .profile-image-wrapper {
    position: relative;
    border-radius: 0;
    overflow: hidden;
    background-color: var(--color-lavender);
    aspect-ratio: 3/4;
    max-height: calc(100svh - 12rem);
    box-shadow: 1.5rem 1.5rem 0 rgba(229, 223, 235, 0.72);
  }

  .profile-image {
    width: 100%;
    height: 100%;
    object-fit: cover;
    filter: saturate(0.88) contrast(1.02);
  }

  .profile-content {
    display: flex;
    flex-direction: column;
    gap: clamp(0.9rem, 1.8vh, 1.5rem);
  }

  .about-name {
    font-family: var(--font-display);
    font-size: clamp(4.5rem, min(8vw, 13vh), 8rem);
    font-weight: 300;
    letter-spacing: -0.055em;
    margin-top: -0.5rem;
    line-height: 0.9;
  }

  .about-roles {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 0;
    border-top: 1px solid var(--color-border);
  }

  .about-role {
    font-family: var(--font-body);
    font-size: 0.62rem;
    letter-spacing: 0.12em;
    text-transform: uppercase;
    color: var(--color-muted);
    border-bottom: 1px solid var(--color-border);
    padding: 0.75rem 0;
    font-weight: 400;
  }

  .about-role:nth-child(odd) {
    padding-right: 1rem;
  }

  .about-role:nth-child(even) {
    padding-left: 1rem;
    border-left: 1px solid var(--color-border);
  }

  .about-summary {
    font-family: var(--font-body);
    font-family: var(--font-display);
    font-size: clamp(1.15rem, 1.8vw, 1.45rem);
    line-height: 1.65;
    font-style: italic;
    color: var(--color-muted);
    letter-spacing: 0.01em;
  }

  .highlights {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 1px;
    background: var(--color-border);
    border: 1px solid var(--color-border);
  }

  .highlight-card {
    padding: 1.5rem 1rem;
    border-radius: 0;
    display: flex;
    flex-direction: column;
    align-items: center;
    text-align: center;
    gap: 0.3rem;
  }

  .highlight-value {
    font-family: var(--font-display);
    font-size: clamp(2rem, 4vw, 3.25rem);
    font-weight: 300;
    letter-spacing: -0.02em;
  }

  .highlight-label {
    font-family: var(--font-body);
    font-size: 0.62rem;
    letter-spacing: 0.2em;
    text-transform: uppercase;
    color: var(--color-muted);
    font-weight: 400;
  }

  /* ── Section 2: Expertise ── */
  .expertise-section {
    border-top: 1px solid var(--color-border);
  }

  .expertise-grid {
    display: grid;
    grid-template-columns: repeat(2, 1fr);
    gap: 1px;
    background: var(--color-border);
    border: 1px solid var(--color-border);
  }

  .expertise-card {
    padding: clamp(2rem, 4vw, 3.5rem);
    border-radius: 0;
    display: flex;
    flex-direction: column;
    gap: 0.85rem;
    min-height: 25rem;
    transition: transform 0.45s var(--ease-editorial), filter 0.45s ease;
  }

  .expertise-card:hover {
    transform: translateY(-5px);
    filter: saturate(1.08);
  }

  .expertise-icon {
    font-size: 1.5rem;
    opacity: 0.65;
    line-height: 1;
    margin-bottom: auto;
  }

  .expertise-title {
    font-family: var(--font-display);
    font-size: clamp(1.75rem, 3vw, 2.6rem);
    font-weight: 300;
    line-height: 1.05;
    letter-spacing: 0.01em;
  }

  .expertise-desc {
    font-family: var(--font-body);
    font-size: 0.86rem;
    line-height: 1.8;
    color: var(--color-muted);
    flex: 1;
    letter-spacing: 0.01em;
  }

  /* ── Section 3: Experience ── */
  .experience-section {
    border-top: 1px solid var(--color-border);
  }

  .experience-list {
    display: flex;
    flex-direction: column;
    gap: 0;
    border-top: 1px solid var(--color-border);
  }

  .job {
    display: flex;
    flex-direction: column;
    gap: 0.4rem;
    padding: clamp(2rem, 4vw, 3.5rem) 0;
    border-radius: 0;
    border-bottom: 1px solid var(--color-border);
    background-color: transparent !important;
  }

  .job-header {
    display: flex;
    justify-content: space-between;
    align-items: baseline;
    gap: 1rem;
    margin-bottom: 0.1rem;
  }

  .job-company {
    font-family: var(--font-display);
    font-size: clamp(2.5rem, 6vw, 5.5rem);
    font-weight: 300;
    letter-spacing: -0.035em;
    letter-spacing: 0.01em;
  }

  .job-period {
    font-family: var(--font-body);
    font-size: 0.68rem;
    letter-spacing: 0.15em;
    color: var(--color-muted);
    text-transform: uppercase;
  }

  .job-role {
    font-family: var(--font-display);
    font-size: 1.3rem;
    font-style: italic;
    font-weight: 300;
    letter-spacing: 0.01em;
  }

  .job-location {
    font-family: var(--font-body);
    font-size: 0.68rem;
    letter-spacing: 0.15em;
    color: var(--color-muted);
    text-transform: uppercase;
  }

  .job-description {
    font-family: var(--font-body);
    font-size: 0.9rem;
    line-height: 1.8;
    margin-top: 1.25rem;
    max-width: 850px;
    letter-spacing: 0.01em;
  }

  /* ── Shared ── */
  .skill-list {
    display: flex;
    flex-wrap: wrap;
    gap: 0.4rem;
    margin-top: 1rem;
  }

  .skill-tag {
    font-family: var(--font-body);
    font-size: 0.62rem;
    padding: 0.3rem 0.7rem;
    border-radius: 0;
    background-color: transparent;
    border: 1px solid rgba(0, 0, 0, 0.18);
    letter-spacing: 0.08em;
    text-transform: uppercase;
  }

  /* ── Responsive ── */
  @media (max-width: 1024px) {
    .profile-grid {
      gap: 3.5rem;
    }
  }

  @media (max-width: 768px) {
    .section {
      padding: 3rem var(--page-pad);
    }

    .profile-grid {
      grid-template-columns: 1fr;
      gap: 2.5rem;
    }

    .profile-section {
      min-height: auto;
      display: block;
    }

    .profile-image-wrapper {
      position: static;
      aspect-ratio: 4/5;
      max-height: none;
    }

    .about-name {
      font-size: clamp(4rem, 17vw, 7rem);
    }

    .expertise-grid {
      grid-template-columns: 1fr 1fr;
    }
  }

  @media (max-width: 480px) {
    .about-roles {
      grid-template-columns: 1fr;
    }

    .about-role:nth-child(even) {
      padding-left: 0;
      border-left: 0;
    }

    .highlights {
      grid-template-columns: 1fr;
    }

    .expertise-grid {
      grid-template-columns: 1fr;
    }

    .expertise-card {
      min-height: 21rem;
    }

    .job-header {
      align-items: flex-start;
      flex-direction: column;
    }
  }
</style>
