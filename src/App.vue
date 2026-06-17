<script setup lang="ts">
import { onMounted } from 'vue';
import Navbar from './components/Navbar.vue';
import HeroSection from './components/HeroSection.vue';
import LifestyleSection from './components/LifestyleSection.vue';
import CourtsSection from './components/CourtsSection.vue';
import CoachesSection from './components/CoachesSection.vue';
import MembershipSection from './components/MembershipSection.vue';
import FaqSection from './components/FaqSection.vue';
import LocationSection from './components/LocationSection.vue';
import FooterSection from './components/FooterSection.vue';

// Intersection Observer for scroll animations
onMounted(() => {
  const observerOptions = {
    root: null,
    rootMargin: '0px',
    threshold: 0.15
  };

  const observer = new IntersectionObserver((entries, observer) => {
    entries.forEach(entry => {
      if (entry.isIntersecting) {
        entry.target.classList.add('is-visible');
        observer.unobserve(entry.target);
      }
    });
  }, observerOptions);

  const revealElements = document.querySelectorAll('.reveal-up');
  revealElements.forEach(el => observer.observe(el));
});
</script>

<template>
  <div class="app-container">
    <Navbar />
    <main>
      <HeroSection />
      <LifestyleSection />
      <CourtsSection />
      <CoachesSection />
      <MembershipSection />
      <FaqSection />
      <LocationSection />
    </main>
    <FooterSection />
  </div>
</template>

<style scoped>
.app-container {
  min-height: 100vh;
  display: flex;
  flex-direction: column;
}
main {
  flex: 1;
}
</style>
