<script setup lang="ts">
import { ref, computed, onMounted, onUnmounted } from 'vue';

const slides = [
  { 
    id: 1, 
    image: 'https://placehold.co/1200x600/1C3609/FFFFFF?text=Lifestyle+Image+1', 
    title: 'A space where sport\nmeets lifestyle.', 
    subtitle: 'Built for those who value quality play\nand meaningful connection.', 
    action: 'Host Now' 
  },
  { 
    id: 2, 
    image: 'https://placehold.co/1200x600/1C3609/FFFFFF?text=Lifestyle+Image+2', 
    title: 'Experience our\npremium courts.', 
    subtitle: 'State of the art facilities\ndesigned for champions.', 
    action: 'Book Now' 
  }
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
  slideInterval = setInterval(nextSlide, 6000);
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
  <section class="lifestyle">
    <div class="lifestyle-bg reveal-up">
      
      <!-- Slider Backgrounds -->
      <div 
        class="slide-bg" 
        v-for="(slide, index) in slides" 
        :key="slide.id"
        :class="{ active: currentSlide === index }"
      >
        <img :src="slide.image" :alt="'Lifestyle Slide ' + slide.id" />
      </div>

      <div class="gradient-overlay"></div>
      
      <div class="content-wrapper">
        <div class="container slide-content">
          <transition name="fade-slide" mode="out-in">
            <div :key="currentSlide" class="text-content">
              <h2>{{ slide.title }}</h2>
              <p>{{ slide.subtitle }}</p>
              <!-- Arrow symbol on the right side based on image -->
              <div class="arrow-right">›</div>
            </div>
          </transition>
          
          <!-- Slider Navigation & Action -->
          <div class="action-wrapper">
            <!-- Left: Action Button -->
            <transition name="fade-slide" mode="out-in">
              <button :key="currentSlide" class="btn-read-more">
                {{ slide.action }}
              </button>
            </transition>
            
            <!-- Right: Dots -->
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
        </div>
      </div>
      
    </div>
  </section>
</template>

<style scoped>
.lifestyle {
  padding: 0 24px;
  margin-top: -40px; 
  position: relative;
  z-index: 5;
  margin-bottom: var(--spacing-section);
}

.lifestyle-bg {
  position: relative;
  width: 100%;
  max-width: 1400px;
  margin: 0 auto;
  border-radius: var(--border-radius-lg);
  overflow: hidden;
  height: 600px;
  box-shadow: 0 24px 48px rgba(0,0,0,0.3);
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
  transition: transform 6s ease-out;
}

.slide-bg.active img {
  transform: scale(1);
}

.gradient-overlay {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background: linear-gradient(135deg, rgba(28, 54, 9, 0.9) 0%, rgba(28, 54, 9, 0.1) 60%, rgba(0,0,0,0.6) 100%);
  z-index: 1;
}

.content-wrapper {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  z-index: 2;
  display: flex;
  flex-direction: column;
}

.slide-content {
  height: 100%;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  padding: 80px 24px 40px;
}

.text-content {
  max-width: 500px;
  position: relative;
}

.text-content h2 {
  font-size: 42px;
  font-weight: 700;
  margin-bottom: 16px;
  line-height: 1.1;
  white-space: pre-line;
}

.text-content p {
  font-size: 16px;
  color: var(--color-secondary);
  line-height: 1.5;
  white-space: pre-line;
}

.arrow-right {
  position: absolute;
  right: -60px;
  top: 50%;
  transform: translateY(-50%);
  font-size: 40px;
  font-weight: 300;
  color: var(--color-primary);
  opacity: 0.8;
}

.action-wrapper {
  display: flex;
  justify-content: space-between;
  align-items: flex-end;
  width: 100%;
}

.btn-read-more {
  background-color: rgba(28, 54, 9, 0.8);
  color: var(--color-primary);
  border: 1px solid var(--color-card-border);
  padding: 12px 32px;
  border-radius: var(--border-radius-lg);
  font-weight: 500;
  font-size: 14px;
  transition: all var(--transition-fast);
  backdrop-filter: blur(8px);
}

.btn-read-more:hover {
  background-color: var(--color-primary);
  color: var(--color-background);
  transform: translateY(-2px);
}

.slider-dots {
  display: flex;
  gap: 8px;
  padding-bottom: 12px;
}

.dot {
  width: 6px;
  height: 6px;
  border-radius: 50%;
  background-color: rgba(255, 255, 255, 0.3);
  cursor: pointer;
  transition: all var(--transition-fast);
}

.dot.active {
  background-color: var(--color-primary);
  width: 18px;
  border-radius: 3px;
}

/* Animations */
.fade-slide-enter-active,
.fade-slide-leave-active {
  transition: all 0.5s ease;
}
.fade-slide-enter-from {
  opacity: 0;
  transform: translateY(15px);
}
.fade-slide-leave-to {
  opacity: 0;
  transform: translateY(-15px);
}

@media (max-width: 768px) {
  .lifestyle {
    margin-top: 0;
    margin-bottom: var(--spacing-section-mobile);
  }
  
  .lifestyle-bg {
    height: 500px;
    border-radius: var(--border-radius-md);
  }
  
  .text-content h2 {
    font-size: 32px;
  }
  
  .arrow-right {
    right: 0;
    position: relative;
    top: auto;
    transform: none;
    display: inline-block;
    margin-top: 16px;
  }
}
</style>
