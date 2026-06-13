<script lang="ts">
  import siteData from '$lib/data/site.json';
  import favicon from '$lib/assets/favicon.svg';

  const year = new Date().getFullYear();
</script>

<footer class="footer">
  <div class="footer-inner">

    <!-- CTA -->
    <div class="footer-cta-block">
      <p class="footer-eyebrow">Open to collaboration</p>
      <p class="footer-cta">Let's create<br />something remarkable.</p>
    </div>

    <!-- Rule -->
    <div class="footer-rule"></div>

    <!-- Bottom row -->
    <div class="footer-bottom">
      <div class="footer-identity">
        <img src={favicon} alt="TD" class="footer-monogram" />
        <p class="footer-name">{siteData.name}</p>
      </div>

      <div class="footer-links">
        <a href="mailto:{siteData.contact.email}" class="footer-link">
          <i class="fa-regular fa-envelope"></i>
          {siteData.contact.email}
        </a>
        <a href={siteData.contact.linkedin} target="_blank" rel="noopener noreferrer" class="footer-link">
          <i class="fa-brands fa-linkedin-in"></i>
          LinkedIn
        </a>
      </div>
    </div>

    <!-- Copyright -->
    <p class="footer-copy">© {year} {siteData.name}. All rights reserved.</p>

  </div>
</footer>

<style>
  .footer {
    border-top: 1px solid var(--color-border);
    margin-top: 8rem;
  }

  .footer-inner {
    max-width: var(--page-max);
    margin: 0 auto;
    padding: 5rem var(--page-pad) 3rem;
    display: flex;
    flex-direction: column;
  }

  /* CTA */
  .footer-cta-block {
    display: flex;
    flex-direction: column;
    gap: 1.5rem;
    padding-bottom: 5rem;
  }

  .footer-eyebrow {
    font-family: var(--font-body);
    font-size: 0.65rem;
    letter-spacing: 0.38em;
    text-transform: uppercase;
    color: var(--color-muted);
    font-weight: 400;
  }

  .footer-cta {
    font-family: var(--font-display);
    font-size: clamp(2.8rem, 6vw, 5rem);
    font-weight: 300;
    color: var(--color-text);
    line-height: 1.05;
    letter-spacing: -0.02em;
  }

  /* Rule */
  .footer-rule {
    border-top: 1px solid var(--color-border);
  }

  /* Bottom row */
  .footer-bottom {
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 2.25rem 0 1.75rem;
    gap: 2rem;
  }

  .footer-identity {
    display: flex;
    align-items: center;
    gap: 1rem;
  }

  .footer-monogram {
    width: 2.5rem;
    height: 2.5rem;
    opacity: 0.85;
    flex-shrink: 0;
  }

  .footer-name {
    font-family: var(--font-display);
    font-size: 1.1rem;
    font-weight: 300;
    letter-spacing: 0.06em;
    text-transform: uppercase;
    color: var(--color-text);
    line-height: 1;
  }

  /* Links */
  .footer-links {
    display: flex;
    flex-direction: column;
    align-items: flex-end;
    gap: 0.65rem;
  }

  .footer-link {
    font-family: var(--font-body);
    font-size: 0.75rem;
    color: var(--color-muted);
    letter-spacing: 0.08em;
    display: flex;
    align-items: center;
    gap: 0.55rem;
    transition: color 0.25s;
  }

  .footer-link:hover {
    color: var(--color-text);
  }

  .footer-link i {
    font-size: 0.7rem;
    opacity: 0.65;
  }

  /* Copyright */
  .footer-copy {
    font-family: var(--font-body);
    font-size: 0.58rem;
    letter-spacing: 0.18em;
    text-transform: uppercase;
    color: var(--color-muted);
    opacity: 0.5;
    padding-top: 0.75rem;
    border-top: 1px solid var(--color-border);
  }

  @media (max-width: 640px) {
    .footer-cta {
      font-size: clamp(2rem, 8vw, 3rem);
    }

    .footer-bottom {
      flex-direction: column;
      align-items: flex-start;
      gap: 2rem;
    }

    .footer-links {
      align-items: flex-start;
    }
  }
</style>
