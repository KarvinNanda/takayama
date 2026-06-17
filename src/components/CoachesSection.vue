<script setup lang="ts">
const coaches = [
  { id: 1, name: 'Coach 1', image: 'https://placehold.co/400x480/1C3609/FFFFFF?text=Coach+1' },
  { id: 2, name: 'Coach 2', image: 'https://placehold.co/400x480/1C3609/FFFFFF?text=Coach+2' },
  { id: 3, name: 'Coach 3', image: 'https://placehold.co/400x480/1C3609/FFFFFF?text=Coach+3' },
];
</script>

<template>
  <section class="section coaches">
    <div class="container">
      <h2 class="section-title reveal-up">Meet Our Coach</h2>
      
      <div class="coaches-grid">
        <div 
          class="coach-card reveal-up" 
          v-for="(coach, index) in coaches" 
          :key="coach.id"
          :style="{ transitionDelay: `${index * 0.2}s` }"
        >
          <img :src="coach.image" :alt="coach.name" />
        </div>
      </div>
      
      <div class="action-wrapper reveal-up" style="transition-delay: 0.6s;">
        <div class="pagination-dots">
          <span class="dot active"></span>
          <span class="dot"></span>
          <span class="dot"></span>
        </div>
        <button class="btn-read-more">Read More</button>
      </div>
    </div>
  </section>
</template>

<style scoped>
.section-title {
  font-size: 32px;
  font-weight: 700;
  margin-bottom: 40px;
}

.coaches-grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 24px;
  margin-bottom: 48px;
}

.coach-card {
  position: relative;
  width: 100%;
  padding-bottom: 120%; /* Portrait aspect ratio */
  border-radius: var(--border-radius-md);
  overflow: hidden;
}

/* Specific styling based on the design where middle image is slightly offset or just rounded */
.coach-card img {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  object-fit: cover;
  transition: transform var(--transition-slow);
}

.coach-card:hover img {
  transform: scale(1.05);
}

/* Simulating the diagonal cut effect on the third card from design */
.coach-card:nth-child(3) {
  clip-path: polygon(0 40%, 100% 0, 100% 100%, 0% 100%);
}

/* Simulating the diagonal cut on the first card */
.coach-card:nth-child(1) {
  clip-path: polygon(0 0, 100% 0, 100% 100%, 0 85%);
}

.action-wrapper {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 24px;
}

.pagination-dots {
  display: flex;
  gap: 8px;
}

.dot {
  width: 8px;
  height: 8px;
  border-radius: 50%;
  background-color: var(--color-card-border);
  transition: background-color var(--transition-fast);
}

.dot.active {
  background-color: var(--color-primary);
}

.btn-read-more {
  background-color: var(--color-dark-green);
  color: var(--color-primary);
  border: 1px solid var(--color-card-border);
  padding: 12px 32px;
  border-radius: var(--border-radius-lg);
  font-weight: 500;
  font-size: 14px;
  transition: all var(--transition-fast);
}

.btn-read-more:hover {
  background-color: var(--color-primary);
  color: var(--color-background);
}

@media (max-width: 768px) {
  .coaches-grid {
    display: flex;
    overflow-x: auto;
    scroll-snap-type: x mandatory;
    gap: 16px;
    padding-bottom: 24px;
    margin: 0 -24px;
    padding-left: 24px;
    padding-right: 24px;
    scrollbar-width: none;
  }
  
  .coaches-grid::-webkit-scrollbar {
    display: none;
  }
  
  .coach-card {
    min-width: 85vw;
    scroll-snap-align: center;
    padding-bottom: 110%; /* Slightly taller on mobile for a good portrait view */
    clip-path: none !important; /* Keep it simple rectangle with rounded corners on mobile */
    border-radius: var(--border-radius-lg);
  }
}
</style>
