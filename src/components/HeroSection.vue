<script setup lang="ts">
import { ref, computed, onMounted, onUnmounted } from 'vue';

const slides = [
  { id: 1, image: 'https://placehold.co/1200x800/1C3609/FFFFFF?text=Hero+Image+1', title: 'Play Padel at\na Higher Standard.', subtitle: 'Premium courts. Curated community.\nElevated experience.', action: 'Get to know more' },
  { id: 2, image: 'https://placehold.co/1200x800/1C3609/FFFFFF?text=Hero+Image+2', title: 'Premium courts.', subtitle: 'Engineered for optimal play.', action: 'Explore Facilities' }
];

const currentSlide = ref(0);
const slide = computed(() => slides[currentSlide.value]!);
let slideInterval: any = null;

const nextSlide = () => {
  currentSlide.value = (currentSlide.value + 1) % slides.length;
};

const setSlide = (index: number) => {
  currentSlide.value = index;
  resetInterval();
};

const startInterval = () => {
  slideInterval = setInterval(nextSlide, 5000);
};

const resetInterval = () => {
  if (slideInterval) clearInterval(slideInterval);
  startInterval();
};

onMounted(() => {
  startInterval();
});

onUnmounted(() => {
  if (slideInterval) clearInterval(slideInterval);
});
</script>

<template>
  <div class="hero-wrapper">
    <!-- Slider Background -->
    <section class="hero-slider">
      <div 
        class="slide-bg" 
        v-for="(slide, index) in slides" 
        :key="slide.id"
        :class="{ active: currentSlide === index }"
      >
        <img :src="slide.image" :alt="'Slide ' + slide.id" />
        <div class="overlay"></div>
      </div>
      
      <div class="container hero-content-overlay">
        <!-- Text Content -->
        <div class="hero-text">
          <transition name="fade-slide" mode="out-in">
            <div :key="currentSlide" class="text-content">
              <h1>{{ slide.title }}</h1>
              <p>{{ slide.subtitle }}</p>
              <button class="text-btn">
                {{ slide.action }}
                <span class="arrow">›</span>
              </button>
            </div>
          </transition>
          
          <!-- Slider Dots -->
          <div class="slider-dots">
            <span 
              v-for="(_, index) in slides" 
              :key="index"
              class="dot"
              :class="{ active: currentSlide === index }"
              @click="setSlide(index)"
            ></span>
          </div>
        </div>

        <!-- Desktop Hero Card -->
        <div class="hero-card desktop-card reveal-up" style="transition-delay: 0.2s;">
          <div class="card-header">
            <h2>Takayama<br>Premier Padel Club</h2>
            <p class="location-text">BSD, Tangerang</p>
          </div>
          <div class="card-body">
            <div class="divider"></div>
            <div class="first-class">
              <span>First Class Free*</span>
              <div class="avatar-placeholder"></div>
            </div>
            <div class="card-actions">
              <button class="btn-solid">Book Now</button>
              <button class="btn-outline">View Courts</button>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- Mobile Hero Card (Appears below hero on mobile) -->
    <div class="container mobile-card-wrapper">
      <div class="hero-card mobile-card reveal-up">
        <div class="card-header">
          <h2>Takayama<br>Premier Padel Club</h2>
          <p class="location-text">BSD, Tangerang</p>
        </div>
        <div class="card-body">
          <div class="divider"></div>
          <div class="first-class">
            <span>First Class Free*</span>
            <div class="avatar-placeholder"></div>
          </div>
          <div class="card-actions">
            <button class="btn-solid">Book Now</button>
            <button class="btn-outline">View Courts</button>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped>
.hero-wrapper {
  position: relative;
  width: 100%;
}

.hero-slider {
  position: relative;
  min-height: 100vh;
  display: flex;
  align-items: center;
  padding-top: 80px;
  overflow: hidden;
}

.slide-bg {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  z-index: -1;
  opacity: 0;
  transition: opacity 1s ease-in-out;
}

.slide-bg.active {
  opacity: 1;
}

.slide-bg img {
  width: 100%;
  height: 100%;
  object-fit: cover;
  object-position: center;
  transform: scale(1.02); 
}

.overlay {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background: linear-gradient(to right, rgba(28, 54, 9, 0.8) 0%, rgba(28, 54, 9, 0.2) 100%);
}

.hero-content-overlay {
  display: flex;
  justify-content: space-between;
  align-items: center;
  width: 100%;
  gap: 40px;
  position: relative;
  z-index: 2;
}

.hero-text {
  flex: 1;
  display: flex;
  flex-direction: column;
  gap: 32px;
}

.text-content {
  display: flex;
  flex-direction: column;
  align-items: flex-start;
}

.text-content h1 {
  font-size: 64px;
  line-height: 1.1;
  margin-bottom: 16px;
  font-weight: 700;
  white-space: pre-line;
}

.text-content p {
  font-size: 18px;
  color: var(--color-secondary);
  margin-bottom: 24px;
  line-height: 1.4;
  white-space: pre-line;
}

.text-btn {
  color: var(--color-primary);
  font-size: 18px;
  font-weight: 500;
  display: inline-flex;
  align-items: center;
  gap: 8px;
  transition: transform var(--transition-fast);
}

.text-btn .arrow {
  font-size: 24px;
  line-height: 1;
}

.text-btn:hover {
  transform: translateX(8px);
}

.slider-dots {
  display: flex;
  gap: 8px;
}

.dot {
  width: 8px;
  height: 8px;
  border-radius: 50%;
  background-color: rgba(255, 255, 255, 0.3);
  cursor: pointer;
  transition: background-color var(--transition-fast), width var(--transition-fast);
}

.dot.active {
  background-color: var(--color-primary);
  width: 24px;
  border-radius: 4px;
}

/* Animations */
.fade-slide-enter-active,
.fade-slide-leave-active {
  transition: all 0.5s ease;
}
.fade-slide-enter-from {
  opacity: 0;
  transform: translateY(20px);
}
.fade-slide-leave-to {
  opacity: 0;
  transform: translateY(-20px);
}

/* Card Styling */
.hero-card {
  background-color: var(--color-primary);
  color: var(--color-background);
  border-radius: var(--border-radius-md);
  padding: 40px;
  width: 100%;
  max-width: 450px;
  box-shadow: 0 20px 40px rgba(0,0,0,0.2);
}

.card-header h2 {
  font-size: 28px;
  font-weight: 700;
  margin-bottom: 8px;
  line-height: 1.2;
}

.location-text {
  font-size: 14px;
  color: #555;
  margin-bottom: 24px;
  font-weight: 500;
}

.divider {
  width: 100%;
  height: 1px;
  background-color: #ddd;
  margin-bottom: 16px;
}

.first-class {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 24px;
  font-size: 14px;
  font-weight: 500;
}

.avatar-placeholder {
  width: 36px;
  height: 36px;
  border-radius: 50%;
  background-color: #eee;
  border: 2px solid #fff;
  box-shadow: 0 2px 8px rgba(0,0,0,0.1);
}

.card-actions {
  display: flex;
  gap: 12px;
}

.btn-outline, .btn-solid {
  flex: 1;
  padding: 14px 0;
  border-radius: var(--border-radius-lg);
  font-weight: 500;
  font-size: 14px;
  transition: all var(--transition-fast);
}

.btn-outline {
  border: 1px solid var(--color-background);
  color: var(--color-background);
}

.btn-outline:hover {
  background-color: rgba(28, 54, 9, 0.05);
}

.btn-solid {
  background-color: var(--color-background);
  color: var(--color-primary);
  border: 1px solid var(--color-background);
}

.btn-solid:hover {
  background-color: var(--color-dark-green);
}

/* Mobile vs Desktop Card Handling */
.mobile-card-wrapper {
  display: none;
}

@media (max-width: 768px) {
  .hero-slider {
    min-height: 80vh;
    padding-top: 100px;
    align-items: flex-end;
    padding-bottom: 40px;
  }
  
  .overlay {
    background: linear-gradient(to bottom, rgba(28, 54, 9, 0.5) 0%, rgba(28, 54, 9, 0.9) 100%);
  }
  
  .hero-content-overlay {
    flex-direction: column;
    align-items: flex-start;
  }
  
  .text-content h1 {
    font-size: 40px;
  }
  
  .desktop-card {
    display: none; /* Hide card inside hero on mobile */
  }
  
  .mobile-card-wrapper {
    display: flex;
    justify-content: center;
    margin-top: -30px; /* Pull it slightly up over the bottom edge of hero */
    margin-bottom: 40px;
    position: relative;
    z-index: 10;
  }
  
  .hero-card {
    padding: 32px 24px;
    box-shadow: 0 10px 30px rgba(0,0,0,0.15);
  }
}
</style>
