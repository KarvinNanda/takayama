<script setup lang="ts">
const courts = [
  {
    id: 1,
    title: 'VIP Court',
    image: 'https://placehold.co/600x450/1C3609/FFFFFF?text=VIP+Court',
    description: 'Experience premium padel with our fully enclosed VIP court featuring panoramic glass, climate control, and a private lounge area for you and your guests.'
  },
  {
    id: 2,
    title: 'Regular Court',
    image: 'https://placehold.co/600x450/1C3609/FFFFFF?text=Regular+Court',
    description: 'Professional grade outdoor courts built to WPT standards. High quality turf and LED lighting ensure the perfect game conditions any time of day.'
  }
];
</script>

<template>
  <section class="section courts">
    <div class="container courts-grid">
      <div 
        class="court-card reveal-up" 
        v-for="(court, index) in courts" 
        :key="court.id"
        :style="{ transitionDelay: `${index * 0.2}s` }"
      >
        <div class="court-image">
          <img :src="court.image" :alt="court.title" />
          <button class="court-badge">{{ court.title }}</button>
        </div>
        <p class="court-desc">{{ court.description }}</p>
      </div>
    </div>
  </section>
</template>

<style scoped>
.courts-grid {
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  gap: 40px;
}

.court-card {
  display: flex;
  flex-direction: column;
  gap: 24px;
}

.court-image {
  position: relative;
  width: 100%;
  padding-bottom: 75%; /* 4:3 Aspect Ratio */
  border-radius: var(--border-radius-md);
  overflow: hidden;
}

.court-image img {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  object-fit: cover;
  transition: transform var(--transition-slow);
}

.court-card:hover .court-image img {
  transform: scale(1.05);
}

.court-badge {
  position: absolute;
  bottom: 24px;
  left: 50%;
  transform: translateX(-50%);
  background-color: var(--color-dark-green);
  color: var(--color-primary);
  padding: 10px 24px;
  border-radius: var(--border-radius-lg);
  font-weight: 500;
  font-size: 14px;
  white-space: nowrap;
  box-shadow: 0 4px 12px rgba(0,0,0,0.2);
  border: 1px solid rgba(255,255,255,0.1);
  transition: background-color var(--transition-fast);
}

.court-card:hover .court-badge {
  background-color: var(--color-background);
}

.court-desc {
  color: var(--color-secondary);
  font-size: 15px;
  line-height: 1.6;
}

@media (max-width: 768px) {
  .courts-grid {
    display: flex;
    overflow-x: auto;
    scroll-snap-type: x mandatory;
    gap: 16px;
    padding-bottom: 24px; /* Space for scrollbar */
    margin: 0 -24px;
    padding-left: 24px;
    padding-right: 24px;
    scrollbar-width: none; /* Firefox */
  }
  
  .courts-grid::-webkit-scrollbar {
    display: none; /* Safari and Chrome */
  }
  
  .court-card {
    min-width: 85vw;
    scroll-snap-align: center;
  }
}
</style>
