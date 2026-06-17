<script setup lang="ts">
const footerLinks = [
  {
    title: 'Explore',
    links: [
      'Select Your Location',
      'Our Mission, Vision & Values',
      'FAQ (including Mobile App)',
      'Press',
      'US Franchising',
      'International Franchising',
      'Customer Service'
    ]
  },
  {
    title: 'Company',
    links: [
      'Global Studios',
      'Jobs',
      'Articles',
      'Shop',
      'Real Estate',
      'Do Not Sell My Information',
      'Affordable Care Act: Transparency in Coverage'
    ]
  },
  {
    title: 'Legal',
    links: [
      'Cookies Settings',
      'Privacy Policy',
      'Terms of Use',
      'Promotion Terms',
      'Accessibility Statement',
      'Legal (Privacy & Terms)'
    ]
  }
];
</script>

<template>
  <footer class="footer">
    <div class="container footer-container">
      
      <div class="footer-top reveal-up">
        <div class="social-links">
          <a href="#" class="social-icon">
            <!-- IG -->
            <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><rect x="2" y="2" width="20" height="20" rx="5" ry="5"></rect><path d="M16 11.37A4 4 0 1 1 12.63 8 4 4 0 0 1 16 11.37z"></path><line x1="17.5" y1="6.5" x2="17.51" y2="6.5"></line></svg>
          </a>
          <a href="#" class="social-icon">
            <!-- X (Twitter) -->
            <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M4 4l11.733 16h4.267l-11.733 -16z"></path><path d="M4 20l6.768 -6.768m2.46 -2.46l6.772 -6.772"></path></svg>
          </a>
          <a href="#" class="social-icon">
            <!-- WhatsApp -->
            <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M21 11.5a8.38 8.38 0 0 1-.9 3.8 8.5 8.5 0 0 1-7.6 4.7 8.38 8.38 0 0 1-3.8-.9L3 21l1.9-5.7a8.38 8.38 0 0 1-.9-3.8 8.5 8.5 0 0 1 4.7-7.6 8.38 8.38 0 0 1 3.8-.9h.5a8.48 8.48 0 0 1 8 8v.5z"></path></svg>
          </a>
          <a href="#" class="social-icon">
            <!-- TikTok -->
            <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M9 12a4 4 0 1 0 4 4V4a5 5 0 0 0 5 5"></path></svg>
          </a>
        </div>
        
        <h2 class="cancellation-text">Membership Cancellation</h2>
      </div>

      <div class="footer-links reveal-up" style="transition-delay: 0.2s;">
        <div class="links-grid">
          <div class="link-col" v-for="col in footerLinks" :key="col.title">
            <ul class="link-list">
              <li v-for="link in col.links" :key="link">
                <a href="#">{{ link }}</a>
              </li>
            </ul>
          </div>
        </div>
      </div>
      
    </div>
  </footer>
</template>

<style scoped>
.footer {
  background-color: #000000;
  padding: 80px 0 60px;
  color: var(--color-primary);
}

.footer-container {
  display: flex;
  flex-direction: column;
  align-items: center;
}

.footer-top {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 32px;
  margin-bottom: 64px;
}

.social-links {
  display: flex;
  gap: 24px;
}

.social-icon {
  width: 28px;
  height: 28px;
  color: var(--color-primary);
  transition: transform var(--transition-fast), color var(--transition-fast);
}

.social-icon:hover {
  transform: translateY(-2px);
  color: var(--color-secondary);
}

.social-icon svg {
  width: 100%;
  height: 100%;
}

.cancellation-text {
  font-size: 28px;
  font-weight: 700;
  letter-spacing: 0.5px;
}

.footer-links {
  width: 100%;
  max-width: 900px;
}

.links-grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 40px;
  width: 100%;
}

.link-list {
  display: flex;
  flex-direction: column;
  gap: 16px;
}

.link-list a {
  color: var(--color-primary);
  font-size: 13px;
  font-weight: 400;
  opacity: 0.9;
  transition: opacity var(--transition-fast), padding-left var(--transition-fast);
  line-height: 1.4;
}

.link-list a:hover {
  opacity: 1;
  padding-left: 4px; /* Subtle hover effect */
}

@media (max-width: 768px) {
  .footer {
    padding: 60px 0 40px;
  }
  
  .cancellation-text {
    font-size: 22px;
    text-align: center;
  }

  .links-grid {
    grid-template-columns: 1fr;
    gap: 32px;
  }
  
  .link-col {
    text-align: center;
  }
  
  .link-list a:hover {
    padding-left: 0;
  }
}
</style>
