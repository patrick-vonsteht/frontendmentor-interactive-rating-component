<script setup>
import { ref } from 'vue';

import RatingForm from './components/RatingForm.vue'
import RatingThankYou from './components/RatingThankYou.vue'

const rating = ref(0);
const flowStep = ref(1);

function handleRatingFormSubmit(submittedRating) {
  rating.value = submittedRating
  flowStep.value++
}
</script>

<template>
  <main>
    <RatingForm v-if="flowStep === 1" @submit="(submittedRating) => handleRatingFormSubmit(submittedRating)"/>
    <RatingThankYou v-if="flowStep === 2" :selectedRating="rating"/>
  </main>

  <footer>
    <div class="attribution">
      Challenge by <a href="https://www.frontendmentor.io?ref=challenge" target="_blank">Frontend Mentor</a>.
      Coded by <a href="#">Patrick von Steht</a>.
    </div>
  </footer>
</template>

<style>
@import './assets/reset.css';
@import './assets/attribution.css';

:root {
  --clr-accent-1: hsl(0, 0%, 100%);
  --clr-accent-2: hsl(25, 97%, 53%);
  --clr-text: hsl(217, 12%, 64%);
  --clr-bg-1: hsl(216, 12%, 8%);
  --clr-bg-2: hsl(213, 19%, 18%);
  --clr-bg-3: hsl(213, 19%, 25%);
}

body {
  display: grid;
  justify-content: center;
  align-content: center;

  color: var(--clr-text);
  background-color: var(--clr-bg-1);

  font: 0.875rem "Overpass", sans-serif;

  margin: 1rem;
}

.container {
  background-color: var(--clr-bg-2);
  padding: 2rem;
  border-radius: 20px;
  min-width: 0;
  max-width: 25rem;
}

h1 {
  color: var(--clr-accent-1);
  font-weight: 700;
}
</style>
