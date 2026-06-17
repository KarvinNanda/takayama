<script setup lang="ts">
const benefits = [
  'Priority booking',
  'Access to community',
  'Special Rates',
  'Private Event',
  'Exclusive Rewards'
];

const tiers = [
  { id: 'regular', name: 'Regular', image: 'https://placehold.co/400x480/1C3609/FFFFFF?text=Regular+Tier' },
  { id: 'priority', name: 'Priority', image: 'https://placehold.co/400x480/1C3609/FFFFFF?text=Priority+Tier' },
  { id: 'corporate', name: 'Corporate', image: 'https://placehold.co/400x480/1C3609/FFFFFF?text=Corporate+Tier' }
];
</script>

<template>
  <section class="section membership">
    <div class="container">
      <div class="membership-header reveal-up">
        <button class="badge">Why Membership?</button>
      </div>
      
      <div class="benefits-grid reveal-up" style="transition-delay: 0.2s;">
        <div class="benefit-item" v-for="benefit in benefits" :key="benefit">
          {{ benefit }}
        </div>
      </div>
      
      <div class="tiers-grid">
        <div 
          class="tier-card reveal-up" 
          v-for="(tier, index) in tiers" 
          :key="tier.id"
          :style="{ transitionDelay: `${0.4 + (index * 0.2)}s` }"
        >
          <img :src="tier.image" :alt="tier.name" />
          <div class="tier-overlay">
            <h3>{{ tier.name }}</h3>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped>
.membership {
  display: flex;
  flex-direction: column;
  align-items: center;
}

.membership-header {
  display: flex;
  justify-content: center;
  margin-bottom: 48px;
}

.badge {
  background-color: rgba(255, 255, 255, 0.1);
  color: var(--color-primary);
  border: 1px solid rgba(255, 255, 255, 0.2);
  padding: 12px 32px;
  border-radius: var(--border-radius-lg);
  font-weight: 500;
  font-size: 16px;
  backdrop-filter: blur(4px);
}

.benefits-grid {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
  gap: 24px 48px;
  margin-bottom: 64px;
  max-width: 800px;
  margin-left: auto;
  margin-right: auto;
}

.benefit-item {
  color: var(--color-primary);
  font-size: 15px;
  font-weight: 400;
}

.tiers-grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 24px;
}

.tier-card {
  position: relative;
  width: 100%;
  padding-bottom: 120%;
  border-radius: var(--border-radius-md);
  overflow: hidden;
  cursor: pointer;
}

.tier-card img {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  object-fit: cover;
  transition: transform var(--transition-slow);
}

.tier-card:hover img {
  transform: scale(1.05);
}

.tier-overlay {
  position: absolute;
  bottom: 0;
  left: 0;
  width: 100%;
  padding: 40px 24px 32px;
  background: linear-gradient(to top, rgba(0,0,0,0.8) 0%, transparent 100%);
  display: flex;
  justify-content: center;
  align-items: flex-end;
}

.tier-card h3 {
  color: var(--color-primary);
  font-size: 24px;
  font-weight: 700;
  text-align: center;
  margin: 0;
  transition: transform var(--transition-fast);
}

.tier-card:hover h3 {
  transform: translateY(-5px);
}

@media (max-width: 768px) {
  .benefits-grid {
    flex-direction: column;
    align-items: center;
    gap: 16px;
    margin-bottom: 40px;
  }
  
  .tiers-grid {
    grid-template-columns: 1fr;
    gap: 16px;
  }
  
  .tier-card {
    padding-bottom: 50%; /* Make them shorter on mobile so they don't take up too much vertical space */
  }
}
</style>
