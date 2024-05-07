<template>
  <button
    class="buy-button"
    :class="{
      'background-color-men': category === 'men\'s clothing',
      'background-color-women': category !== 'men\'s clothing',
    }"
  >
    Buy now
  </button>
</template>
<script>
export default {
  name: "BuyButton",
  props: {
    category: String,
  },
};
</script>
<style scoped>
.buy-button {
  color: var(--white-color);
  padding: 0.5rem 4rem;
  border: none;
  border-radius: 0.25rem;
  cursor: pointer;
}
</style>
