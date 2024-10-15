<script setup>
import { ref } from 'vue'

const emit = defineEmits({
  submit: {
    type: String
  }
})

const selectedRating = ref(undefined)
const validationError = ref('');

function validateForm() {
  if (selectedRating.value) {
    validationError.value = ""
    return true
  } else {
    validationError.value =  "You must pick a rating before submitting the form"
    return false
  }
}

function submitForm() {
  if (validateForm()) {
    emit("submit", selectedRating.value)
  }
}
</script>

<template>
  <div class="ratingform container">
    <img class="ratingform__icon" src="../assets/icon-star.svg" alt="">
    <h1 class="ratingform__heading">How did we do?</h1>
    <p class="ratingform__text">Please let us know how we did with your support request. All
      feedback is appreciated to help us improve our offering!</p>
    <div class="ratingform__ratingbar">
      <label v-for="rating in [1, 2, 3, 4, 5]" :key="rating" class="ratingform__ratingoption">
        <input
          class="ratingform__ratingbutton"
          type="radio" name="ratingform__rating"
          :value="rating"
          v-model="selectedRating"
          @change="validateForm">
        <span class="ratingform__ratingbuttontext">{{ rating }}</span>
      </label>
    </div>
    <button class="ratingform__submitbutton" @click="submitForm">Submit</button>
    <p class="ratingform__validationerror" v-if="validationError">{{ validationError }}</p>
  </div>
</template>

<style scoped>
  .ratingform__icon {
    padding: 1em;
    border-radius: 50%;
    background-color: var(--clr-bg-3);
    margin-bottom: 1.5rem;
  }

  .ratingform__heading {
    margin-bottom: 0.5rem;
  }

  .ratingform__text {
    margin-bottom: 1.5rem;
  }

  .ratingform__ratingbar {
    display: grid;
    grid-template-columns: repeat(5, 1fr);
    grid-gap: 1em;
    margin-bottom: 1.5rem;
  }

  .ratingform__ratingoption {
    display: grid;
  }

  .ratingform__ratingbutton {
    grid-row: 1;
    grid-column: 1;

    aspect-ratio: 1 / 1;

    appearance: none;

    background-color: var(--clr-bg-3);
    border-radius: 50%;
  }

  .ratingform__ratingbutton:hover,
  .ratingform__ratingbutton:focus {
    color: var(--clr-bg-1);
    background-color: var(--clr-accent-2);
    cursor: pointer;
  }

  .ratingform__ratingbutton:checked {
    color: var(--clr-bg-1);
    background-color: var(--clr-accent-1);
  }

  .ratingform__ratingbuttontext {
    grid-row: 1;
    grid-column: 1;

    aspect-ratio: 1 / 1;

    display: flex;
    align-items: center;
    justify-content: center;

    pointer-events: none;

    padding-top: 0.125em;
    font-size: 1.25rem;
    font-weight: 700;
  }

  .ratingform__ratingbutton:checked + .ratingform__ratingbuttontext {
    color: var(--clr-bg-2);
  }

  .ratingform__ratingbutton:hover + .ratingform__ratingbuttontext,
  .ratingform__ratingbutton:focus + .ratingform__ratingbuttontext {
    color: var(--clr-bg-2);
  }

  .ratingform__submitbutton {
    width: 100%;

    padding: 1em 1.5em;
    margin-bottom: 1em;
    background-color: var(--clr-accent-2);
    border-radius: 10em;

    color: var(--clr-bg-2);
    font-weight: 700;
    text-transform: uppercase;
    letter-spacing: 1px;
  }

  .ratingform__submitbutton:hover,
  .ratingform__submitbutton:focus {
    background-color: var(--clr-accent-1);
  }

  .ratingform__validationerror {
    color: var(--clr-accent-2);
  }
</style>
