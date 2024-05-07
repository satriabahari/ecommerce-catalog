<template>
  <button
    class="next-button"
    :class="{
      'border-color-men text-color-men': category === 'men\'s clothing',
      'border-color-women text-color-women': category !== 'men\'s clothing',
      'border-color-unavailable text-color-unavailable':
        (category !== 'men\'s clothing') &
        (category !== 'women\'s clothing'),
    }"
  >
    Next product
  </button>
</template>
<script>
export default {
  name: "NextButton",
  props: {
    category: String,
  },
};
</script>
<style scoped>
.next-button {
  background-color: var(--white-color);
  padding: 0.5rem 4rem;
  border-radius: 0.25rem;
  cursor: pointer;
}
</style>
