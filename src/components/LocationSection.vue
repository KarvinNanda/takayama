<script setup lang="ts">
</script>

<template>
  <section class="section location">
    <div class="container">
      
      <!-- Top: Map -->
      <div class="map-container reveal-up">
        <img src="https://placehold.co/1200x400/1C3609/FFFFFF?text=Map+Location" alt="Map Location" />
      </div>
      
      <!-- Middle: Location Details -->
      <div class="location-details reveal-up" style="transition-delay: 0.2s;">
        <div class="address-info">
          <div class="location-icon">
            <svg width="24" height="24" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
              <path d="M12 2C8.13 2 5 5.13 5 9C5 14.25 12 22 12 22C12 22 19 14.25 19 9C19 5.13 15.87 2 12 2ZM12 11.5C10.62 11.5 9.5 10.38 9.5 9C9.5 7.62 10.62 6.5 12 6.5C13.38 6.5 14.5 7.62 14.5 9C14.5 10.38 13.38 11.5 12 11.5Z" fill="currentColor"/>
            </svg>
          </div>
          <div class="address-text">
            <h3>Easy Access Location</h3>
            <p>Raya Serpong Road, Kilometer 7, No. KM 8, Pakulonan,<br>North Serpong District, South Tangerang City, Banten<br>15325, Indonesia</p>
          </div>
        </div>
        
        <div class="contact-actions">
          <button class="btn-dark-green">
            <span class="icon">✆</span>
            +62 8123 456 789
          </button>
          <button class="btn-dark-green">
            <span class="icon">✉</span>
            hello@takayamapremier.com
          </button>
        </div>
      </div>

      <!-- Divider for Mobile -->
      <div class="mobile-divider reveal-up"></div>

      <!-- Bottom: Brand & Contacts Pre-Footer -->
      <div class="brand-section reveal-up" style="transition-delay: 0.4s;">
        <div class="brand-logo-container">
          <!-- The white chevron logo -->
          <svg class="brand-chevron" viewBox="0 0 100 100" fill="none" xmlns="http://www.w3.org/2000/svg">
            <path d="M50 20 L80 80 L60 80 L40 40 L30 60 L10 60 Z" fill="white"/>
            <circle cx="70" cy="30" r="10" fill="white"/>
          </svg>
          <!-- Small dark circular avatar next to it -->
          <div class="avatar-circle"></div>
        </div>
        
        <div class="mobile-divider second-divider"></div>

        <div class="brand-text-wrapper">
          <h1 class="brand-title">T A K A Y A M A</h1>
          <p class="brand-subtitle">PREMIER PADEL CLUB</p>
          
          <div class="brand-contacts">
            <p><span class="icon">✆</span> +62 8123 456 789</p>
            <p><span class="icon">✉</span> hello@takayamapremier.com</p>
          </div>
        </div>
      </div>
      
    </div>
  </section>
</template>

<style scoped>
.location {
  padding-bottom: 80px;
}

.map-container {
  width: 100%;
  border-radius: var(--border-radius-md);
  overflow: hidden;
  margin-bottom: 40px;
  height: 400px;
  background-color: var(--color-dark-green);
}

.map-container img {
  width: 100%;
  height: 100%;
  object-fit: cover;
}

.location-details {
  display: flex;
  justify-content: space-between;
  align-items: flex-start;
  margin-bottom: 80px;
}

.address-info {
  display: flex;
  gap: 16px;
  max-width: 60%;
}

.location-icon {
  color: var(--color-primary);
  margin-top: 4px;
}

.address-text h3 {
  font-size: 24px;
  font-weight: 700;
  margin-bottom: 12px;
}

.address-text p {
  color: var(--color-secondary);
  font-size: 15px;
  line-height: 1.6;
}

.contact-actions {
  display: flex;
  flex-direction: column;
  gap: 16px;
  min-width: 300px;
}

.btn-dark-green {
  display: flex;
  align-items: center;
  gap: 12px;
  background-color: rgba(255, 255, 255, 0.1);
  color: var(--color-primary);
  border: none;
  padding: 16px 24px;
  border-radius: var(--border-radius-sm);
  font-weight: 400;
  font-size: 14px;
  transition: all var(--transition-fast);
}

.btn-dark-green:hover {
  background-color: rgba(255, 255, 255, 0.2);
}

.mobile-divider {
  display: none;
  width: 100%;
  height: 1px;
  background-color: rgba(255, 255, 255, 0.2);
  margin: 40px 0;
}

/* Brand Section Styling */
.brand-section {
  display: flex;
  flex-direction: column;
  align-items: center;
  text-align: center;
  margin-top: 40px;
}

.brand-logo-container {
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 20px;
  margin-bottom: 40px;
}

.brand-chevron {
  width: 80px;
  height: 80px;
}

.avatar-circle {
  width: 50px;
  height: 50px;
  border-radius: 50%;
  background-color: rgba(0,0,0,0.4);
  border: 2px solid rgba(255,255,255,0.1);
}

.brand-title {
  font-size: 48px;
  font-weight: 700;
  letter-spacing: 8px;
  margin-bottom: 8px;
}

.brand-subtitle {
  font-size: 12px;
  letter-spacing: 4px;
  font-weight: 700;
  color: var(--color-secondary);
  margin-bottom: 32px;
}

.brand-contacts {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 12px;
}

.brand-contacts p {
  display: flex;
  align-items: center;
  gap: 12px;
  color: var(--color-primary);
  font-size: 16px;
}

/* Desktop variations matching Image 5 slightly better */
@media (min-width: 769px) {
  .brand-section {
    align-items: flex-start;
    text-align: left;
    flex-direction: row;
    justify-content: space-between;
  }
  
  .brand-logo-container {
    flex: 1;
    justify-content: center;
  }
  
  .brand-text-wrapper {
    flex: 1;
    display: flex;
    flex-direction: column;
    align-items: flex-start;
  }
  
  .brand-contacts {
    align-items: flex-start;
  }
}

/* Mobile */
@media (max-width: 768px) {
  .location-details {
    flex-direction: column;
    gap: 32px;
    margin-bottom: 0;
  }
  
  .address-info {
    max-width: 100%;
  }
  
  .contact-actions {
    display: none; /* In mobile image 4, these specific buttons aren't shown here, they are merged into brand contacts below */
  }
  
  .map-container {
    height: 250px;
  }
  
  .mobile-divider {
    display: block;
  }
  
  .brand-section {
    align-items: flex-start;
    text-align: left;
    margin-top: 0;
  }
  
  .brand-logo-container {
    width: 100%;
  }
  
  .brand-title {
    font-size: 32px;
    letter-spacing: 4px;
  }
  
  .brand-contacts {
    align-items: flex-start;
  }
}
</style>
