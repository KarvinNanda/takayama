<script setup lang="ts">
import { ref } from 'vue';

const faqs = ref([
  {
    id: 1,
    question: 'How to book?',
    answer: 'You can book a court through our online platform or mobile app up to 7 days in advance. Priority members can book up to 14 days in advance.',
    isOpen: false
  },
  {
    id: 2,
    question: 'Do I need my own equipment?',
    answer: 'No, we provide high-quality padel rackets and balls for rent at our reception desk. However, you are welcome to bring your own equipment if you prefer.',
    isOpen: false
  },
  {
    id: 3,
    question: 'Can beginners play?',
    answer: 'Absolutely! Padel is very easy to pick up. We also offer beginner clinics and private coaching sessions to help you get started.',
    isOpen: false
  },
  {
    id: 4,
    question: 'Cancellation policy?',
    answer: 'Cancellations made more than 24 hours before the booked time will receive a full refund. Late cancellations may be subject to a fee.',
    isOpen: false
  },
  {
    id: 5,
    question: 'Payment methods?',
    answer: 'We accept all major credit cards, Apple Pay, Google Pay, and bank transfers for memberships.',
    isOpen: false
  }
]);

const toggleFaq = (index: number) => {
  faqs.value[index].isOpen = !faqs.value[index].isOpen;
};
</script>

<template>
  <section class="section faq-section">
    <div class="container faq-container">
      
      <div class="faq-left reveal-up">
        <div class="sponsor-placeholder">
          <div class="circle"></div>
          <p>Logo Sponsor</p>
        </div>
      </div>
      
      <div class="faq-right reveal-up" style="transition-delay: 0.2s;">
        <h2 class="section-title">Frequently Asked<br>Questions</h2>
        
        <div class="accordion">
          <div 
            class="accordion-item" 
            v-for="(faq, index) in faqs" 
            :key="faq.id"
            :class="{ 'is-open': faq.isOpen }"
          >
            <button class="accordion-header" @click="toggleFaq(index)">
              <span>{{ faq.question }}</span>
              <span class="icon">{{ faq.isOpen ? '−' : '+' }}</span>
            </button>
            <transition name="accordion-slide">
              <div class="accordion-content" v-show="faq.isOpen">
                <p>{{ faq.answer }}</p>
              </div>
            </transition>
          </div>
        </div>
        
        <div class="faq-action">
          <button class="btn-outline-green">Ask More Questions ></button>
        </div>
      </div>

    </div>
  </section>
</template>

<style scoped>
.faq-container {
  display: flex;
  gap: 80px;
}

.faq-left, .faq-right {
  flex: 1;
}

.sponsor-placeholder {
  background-color: rgba(255, 255, 255, 0.05);
  border-radius: var(--border-radius-lg);
  padding: 80px 40px;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  gap: 32px;
  height: 100%;
  min-height: 400px;
  border: 1px dashed rgba(255, 255, 255, 0.1);
}

.circle {
  width: 120px;
  height: 120px;
  background-color: var(--color-dark-green);
  border-radius: 50%;
}

.sponsor-placeholder p {
  color: var(--color-primary);
  font-size: 18px;
  font-weight: 500;
}

.section-title {
  font-size: 32px;
  font-weight: 700;
  margin-bottom: 32px;
  line-height: 1.2;
}

.accordion {
  display: flex;
  flex-direction: column;
  gap: 16px;
  margin-bottom: 32px;
}

.accordion-item {
  border: 1px solid var(--color-card-border);
  border-radius: var(--border-radius-sm);
  overflow: hidden;
  transition: border-color var(--transition-fast);
}

.accordion-item.is-open {
  border-color: rgba(255, 255, 255, 0.3);
}

.accordion-header {
  width: 100%;
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 16px 24px;
  color: var(--color-primary);
  font-size: 16px;
  font-weight: 400;
  text-align: left;
  transition: background-color var(--transition-fast);
}

.accordion-header:hover {
  background-color: rgba(255, 255, 255, 0.05);
}

.accordion-header .icon {
  font-size: 20px;
  font-weight: 300;
}

.accordion-content {
  padding: 0 24px 24px;
  color: var(--color-secondary);
  font-size: 15px;
  line-height: 1.5;
}

/* Accordion transition */
.accordion-slide-enter-active,
.accordion-slide-leave-active {
  transition: all 0.3s ease;
  max-height: 200px;
  opacity: 1;
}

.accordion-slide-enter-from,
.accordion-slide-leave-to {
  max-height: 0;
  opacity: 0;
  padding-bottom: 0;
  padding-top: 0;
}

.btn-outline-green {
  background: transparent;
  color: var(--color-primary);
  border: 1px solid var(--color-card-border);
  padding: 12px 24px;
  border-radius: var(--border-radius-lg);
  font-weight: 500;
  font-size: 14px;
  transition: all var(--transition-fast);
}

.btn-outline-green:hover {
  background-color: rgba(255, 255, 255, 0.1);
}

@media (max-width: 768px) {
  .faq-container {
    flex-direction: column-reverse;
    gap: 40px;
  }
  
  .sponsor-placeholder {
    min-height: 250px;
    padding: 40px 24px;
  }
}
</style>
