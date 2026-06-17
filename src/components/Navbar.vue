<script setup lang="ts">
import { ref, onMounted, onUnmounted } from 'vue';

const isScrolled = ref(false);

const handleScroll = () => {
  isScrolled.value = window.scrollY > 50;
};

onMounted(() => {
  window.addEventListener('scroll', handleScroll);
});

onUnmounted(() => {
  window.removeEventListener('scroll', handleScroll);
});
</script>

<template>
  <header :class="['navbar', { 'scrolled': isScrolled }]">
    <div class="container nav-container">
      <div class="logo">
        <img src="https://placehold.co/200x50/1C3609/FFFFFF?text=LOGO" alt="Takayama Logo" />
      </div>
      <button class="play-btn">Play Padel</button>
    </div>
  </header>
</template>

<style scoped>
.navbar {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  z-index: 100;
  padding: 24px 0;
  transition: all var(--transition-fast);
}

.navbar.scrolled {
  padding: 16px 0;
  background-color: rgba(28, 54, 9, 0.95);
  backdrop-filter: blur(10px);
  border-bottom: 1px solid var(--color-card-border);
}

.nav-container {
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.logo img {
  height: 32px;
  width: auto;
  object-fit: contain;
}

.play-btn {
  background-color: var(--color-primary);
  color: var(--color-button-text);
  padding: 12px 24px;
  border-radius: var(--border-radius-lg);
  font-weight: 500;
  font-size: 14px;
  transition: transform var(--transition-fast), box-shadow var(--transition-fast);
}

.play-btn:hover {
  transform: translateY(-2px);
  box-shadow: 0 4px 12px rgba(255, 255, 255, 0.2);
}
</style>
