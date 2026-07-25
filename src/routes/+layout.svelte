<script lang="ts">
  import './layout.css';
  import favicon from '$lib/assets/favicon.svg';
  import Header from '$lib/components/Header.svelte';
  import Footer from '$lib/components/Footer.svelte';
  import siteData from '$lib/data/site.json';

  let { children } = $props();
  const siteUrl = 'https://taradevi.studio';
  const profileImageUrl = `${siteUrl}${siteData.profileImage}`;
  const personSchema = {
    '@context': 'https://schema.org',
    '@type': 'Person',
    '@id': `${siteUrl}/#person`,
    name: siteData.name,
    url: siteUrl,
    image: {
      '@type': 'ImageObject',
      '@id': `${siteUrl}/#profile-image`,
      url: profileImageUrl,
      contentUrl: profileImageUrl,
      width: 854,
      height: 1280,
      caption: siteData.name
    },
    jobTitle: 'Senior Creative Producer',
    description: siteData.seo.home.description,
    address: {
      '@type': 'PostalAddress',
      addressLocality: 'Gurugram',
      addressRegion: 'Haryana',
      addressCountry: 'IN'
    },
    sameAs: [siteData.contact.linkedin]
  };
</script>

<svelte:head>
  <link rel="icon" href={favicon} />
  <meta name="author" content={siteData.name} />
  <meta name="theme-color" content="#f5f2ec" />
  <meta name="robots" content="index, follow, max-image-preview:large" />
  <meta property="og:site_name" content={siteData.name} />
  <meta property="og:locale" content="en_IN" />
  <meta name="twitter:card" content="summary_large_image" />
  <script type="application/ld+json">{JSON.stringify(personSchema)}</script>
</svelte:head>

<a class="skip-link" href="#main-content">Skip to content</a>
<Header />
<main id="main-content">
  {@render children()}
</main>
<Footer />

<style>
  main {
    min-height: calc(100vh - 120px);
  }
  .skip-link {
    position: fixed;
    left: 1rem;
    top: 1rem;
    z-index: 1000;
    padding: 0.65rem 1rem;
    background: var(--color-text);
    color: var(--color-bg);
    transform: translateY(-160%);
    transition: transform 0.2s ease;
  }
  .skip-link:focus {
    transform: translateY(0);
  }
</style>
