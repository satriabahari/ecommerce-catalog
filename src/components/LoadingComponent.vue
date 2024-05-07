<template>
  <div class="card">
    <div class="image"></div>
    <div class="flex">
      <div class="section">
        <div class="block"></div>
        <div class="block"></div>
        <div class="breakline"></div>
      </div>
      <div class="description"></div>
      <div class="section">
        <div class="breakline"></div>
        <div class="price"></div>
        <div class="buttons">
          <div class="button"></div>
          <div class="button"></div>
        </div>
      </div>
    </div>
  </div>
</template>
<script setup></script>
<style scoped>
.card {
  display: flex;
  gap: 0 4rem;
  width: 75%;
  min-height: 75%;
  background-color: var(--white-color);
  padding: 3rem;
  border-radius: 0.5rem;
  box-shadow: 2px 2px 4px rgba(0, 0, 0, 0.2),
    -2px -2px 4px rgba(255, 255, 255, 0.4);
}
.flex {
  display: flex;
  flex-direction: column;
  gap: 1rem;
  width: 100%;
  justify-content: space-between;
}
.section {
  display: flex;
  flex-direction: column;
  gap: 1rem;
}
.block {
  width: 100%;
  height: 1rem;
  background-color: var(--light-gray-color);
  border-radius: 0.5rem;
}
.breakline {
  width: 100%;
  height: 0.25rem;
  background-color: var(--light-gray-color);
  border-radius: 0.5rem;
}
.button {
  width: 40%;
  height: 2rem;
  background-color: var(--light-gray-color);
  border-radius: 0.5rem;
}
.buttons {
  display: flex;
  gap: 1rem;
}
.description {
  width: 100%;
  height: 10rem;
  background-color: var(--light-gray-color);
  border-radius: 0.5rem;
}
.price {
  width: 25%;
  height: 1rem;
  background-color: var(--light-gray-color);
  border-radius: 0.5rem;
}
.image {
  width: 500px;
  height: 400px;
  background-color: var(--light-gray-color);
  border-radius: 1rem;
}
</style>
