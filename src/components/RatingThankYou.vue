<script setup>
defineProps({
  selectedRating: {
    type: Number,
    required: true,
  },
})
</script>

<template>
  <div class="ratingty container">
    <img class="ratingty__image" src="../assets/illustration-thank-you.svg" alt="">
    <p class="ratingty__selectiontext">You selected {{ selectedRating }} out of 5</p>
    <h1 class="ratingty__heading">Thank you!</h1>
    <p class="ratingty__text">We appreciate you taking the time to give a rating. If you ever need
      more support, don't hesitate to get in touch!</p>
  </div>
</template>

<style>
  .ratingty {
    text-align: center;
  }

  .ratingty__image {
    display: block;
    margin: 0 auto 1.5rem;
  }

  .ratingty__selectiontext {
    display: inline-block;
    padding: 0.625em 1em;
    margin-bottom: 1rem;

    color: var(--clr-accent-2);
    opacity: 0.7;

    background-color: var(--clr-bg-3);
    border-radius: 10em;
  }

  .ratingty__heading {
    margin-bottom: 1rem;
  }
</style>
