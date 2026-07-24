<script lang="ts">
  import siteData from '$lib/data/site.json';
  import favicon from '$lib/assets/favicon.svg';

  const year = new Date().getFullYear();
</script>

<footer class="footer">
  <div class="footer-inner">

    <!-- CTA block -->
    <div class="footer-cta-block">
      <p class="footer-label">Get in touch</p>
      <p class="footer-cta">Interested in working<br />together? Let's connect!</p>
    </div>

    <!-- Divider -->
    <div class="footer-rule"></div>

    <!-- Bottom row -->
    <div class="footer-bottom">
      <div class="footer-identity">
        <img src={favicon} alt="TD" class="footer-monogram" />
        <p class="footer-name">{siteData.name}</p>
      </div>

      <div class="footer-contact">
        <a href="mailto:{siteData.contact.email}" class="footer-email">
          <i class="fa-regular fa-envelope"></i>
          {siteData.contact.email}
        </a>
        <a href={siteData.contact.linkedin} target="_blank" rel="noopener noreferrer" class="footer-linkedin">
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
    --footer-text: var(--color-text);
    --footer-muted: var(--color-muted);
    --footer-rule: rgba(23, 22, 18, 0.16);
    margin-top: clamp(5rem, 10vw, 10rem);
    background:
      radial-gradient(circle at 85% 20%, rgba(229, 223, 235, 0.72), transparent 28rem),
      linear-gradient(135deg, #e8dfd2, #eee7dc);
    color: var(--footer-text);
  }

  .footer-inner {
    max-width: var(--page-max);
    margin: 0 auto;
    padding: clamp(4rem, 8vw, 7.5rem) var(--page-pad) 2.5rem;
    display: flex;
    flex-direction: column;
    gap: 0;
  }

  /* CTA block */
  .footer-cta-block {
    display: grid;
    grid-template-columns: minmax(7rem, 0.28fr) 1fr;
    gap: clamp(2rem, 6vw, 6rem);
    align-items: start;
    padding-bottom: clamp(4rem, 8vw, 7rem);
  }

  .footer-label {
    font-family: var(--font-body);
    font-size: 0.68rem;
    letter-spacing: 0.3em;
    text-transform: uppercase;
    color: var(--footer-muted);
    font-weight: 400;
  }

  .footer-cta {
    font-family: var(--font-display);
    font-size: clamp(3rem, 7vw, 6.8rem);
    font-style: normal;
    font-weight: 300;
    color: var(--footer-text);
    line-height: 1.06;
    letter-spacing: -0.035em;
    max-width: 980px;
  }

  /* Divider */
  .footer-rule {
    border-top: 1px solid var(--footer-rule);
  }

  /* Bottom row */
  .footer-bottom {
    display: flex;
    justify-content: space-between;
    align-items: flex-start;
    padding: 2rem 0;
    gap: 2rem;
  }

  .footer-identity {
    display: flex;
    align-items: center;
    gap: 1.1rem;
  }

  .footer-monogram {
    width: 2.4rem;
    height: 2.4rem;
    opacity: 0.9;
    flex-shrink: 0;
  }

  .footer-name {
    font-family: var(--font-display);
    font-size: 1.25rem;
    font-weight: 300;
    letter-spacing: 0.06em;
    text-transform: uppercase;
    color: var(--footer-text);
    line-height: 1;
  }

  /* Contact links */
  .footer-contact {
    display: flex;
    align-items: center;
    gap: clamp(1.25rem, 4vw, 3.5rem);
  }

  .footer-email,
  .footer-linkedin {
    font-family: var(--font-body);
    font-size: 0.78rem;
    color: var(--footer-muted);
    letter-spacing: 0.08em;
    display: flex;
    align-items: center;
    gap: 0.6rem;
    transition: color 0.25s ease, transform 0.25s ease;
  }

  .footer-email:hover,
  .footer-linkedin:hover {
    color: var(--footer-text);
    transform: translateY(-2px);
  }

  .footer-email i,
  .footer-linkedin i {
    font-size: 0.7rem;
    opacity: 0.7;
  }

  /* Copyright */
  .footer-copy {
    font-family: var(--font-body);
    font-size: 0.6rem;
    letter-spacing: 0.18em;
    text-transform: uppercase;
    color: var(--footer-muted);
    padding-top: 1.25rem;
    border-top: 1px solid var(--footer-rule);
  }

  @media (max-width: 640px) {
    .footer-cta-block {
      grid-template-columns: 1fr;
      gap: 1.5rem;
    }

    .footer-cta {
      font-size: clamp(2.6rem, 12vw, 4rem);
      line-height: 1.08;
    }

    .footer-bottom {
      flex-direction: column;
      gap: 2rem;
    }

    .footer-contact {
      flex-direction: column;
      align-items: flex-start;
    }
  }
</style>
