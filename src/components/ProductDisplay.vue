<template>
  <main class="container">
    <div
      class="background-category"
      :class="{
        'background-men': product.category === 'men\'s clothing',
        'background-women': product.category !== 'men\'s clothing',
        'background-unavailable':
          (product.category !== 'men\'s clothing') &
          (product.category !== 'women\'s clothing'),
      }"
    />

    <div v-if="loading"><LoadingComponent /></div>
    <div v-else class="card">
      <img
        v-if="product && Object.keys(product).length !== 0"
        :src="product.image"
        :alt="product.title"
        width="300"
      />
      <div
        v-if="product && Object.keys(product).length !== 0"
        class="side-card"
      >
        <div>
          <h1
            class="title"
            :class="{
              'text-color-men': product.category === 'men\'s clothing',
              'text-color-women': product.category !== 'men\'s clothing',
            }"
          >
            {{ product.title }}
          </h1>
          <div class="space-between">
            <p>{{ product.category }}</p>
            <div class="flex gap">
              <p>2.9/5</p>
              <div class="circles">
                <div
                  class="circle"
                  :class="{
                    'background-color-men':
                      product.category === 'men\'s clothing',
                    'background-color-women':
                      product.category !== 'men\'s clothing',
                  }"
                />
                <div
                  class="circle"
                  :class="{
                    'background-color-men':
                      product.category === 'men\'s clothing',
                    'background-color-women':
                      product.category !== 'men\'s clothing',
                  }"
                />
                <div
                  class="circle"
                  :class="{
                    'background-color-men':
                      product.category === 'men\'s clothing',
                    'background-color-women':
                      product.category !== 'men\'s clothing',
                  }"
                />
                <div
                  class="circle"
                  :class="{
                    'border-color-men': product.category === 'men\'s clothing',
                    'border-color-women':
                      product.category !== 'men\'s clothing',
                  }"
                />
                <div
                  class="circle"
                  :class="{
                    'border-color-men': product.category === 'men\'s clothing',
                    'border-color-women':
                      product.category !== 'men\'s clothing',
                  }"
                />
              </div>
            </div>
          </div>
          <BreakLine />
          <p>{{ product.description }}</p>
        </div>
        <div>
          <BreakLine />
          <h3
            :class="{
              'text-color-men': product.category === 'men\'s clothing',
              'text-color-women': product.category !== 'men\'s clothing',
            }"
          >
            ${{ product.price }}
          </h3>
          <div class="buttons">
            <BuyButton :category="product.category" />
            <NextButton
              @click="handleClickNextButton"
              :category="product.category"
            />
          </div>
        </div>
      </div>
      <div v-else class="unavailable">
        <p>This product is unavailable to show</p>
        <NextButton
          @click="handleClickNextButton"
          :category="product.category"
        />
      </div>
    </div>
  </main>
</template>

<script setup>
import { ref, onMounted } from "vue";
import axios from "axios";

import BuyButton from "./BuyButton.vue";
import NextButton from "./NextButton.vue";
import BreakLine from "./BreakLine.vue";
import LoadingComponent from "./LoadingComponent.vue";

const product = ref({});
const index = ref(1);
const loading = ref(true);

const fetchProductByIndex = async (index) => {
  loading.value = true;
  const response = await axios.get(
    `https://fakestoreapi.com/products/${index}`
  );
  loading.value = false;
  return response.data;
};

const setProduct = (data) => {
  if (
    data.category == "men's clothing" ||
    data.category == "women's clothing"
  ) {
    product.value = data;
  } else {
    product.value = {};
  }
};

const handleClickNextButton = async () => {
  if (index.value == 20) {
    index.value = 0;
  }
  if (index.value < 20) {
    index.value++;
  }
  setProduct(await fetchProductByIndex(index.value));
};

onMounted(async () => {
  setProduct(await fetchProductByIndex(index.value));
});
</script>

<style scoped>
.container {
  position: relative;
  height: 100vh;
  background-color: var(--white-color);
}

.background-category {
  height: 70vh;
}

.card {
  display: flex;
  gap: 0 4rem;
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  width: 75%;
  min-height: 75%;
  background-color: var(--white-color);
  padding: 3rem;
  border-radius: 0.5rem;
  box-shadow: 2px 2px 4px rgba(0, 0, 0, 0.2),
    -2px -2px 4px rgba(255, 255, 255, 0.4);
}

.side-card {
  display: flex;
  flex-direction: column;
  justify-content: space-between;
}

.title {
  font-size: 1.5rem;
}

.buttons {
  display: flex;
  gap: 0 1rem;
}

.circles {
  display: flex;
  gap: 0 0.2rem;
  margin-top: 0.2rem;
}

.gap {
  gap: 0 0.5rem;
}

.flex {
  display: flex;
}

.space-between {
  display: flex;
  justify-content: space-between;
  margin-top: 1rem;
}

.item-center {
  align-items: center;
}

.circle {
  border-radius: 100%;
  width: 1rem;
  height: 1rem;
}

.unavailable {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  margin: auto;
  gap: 1rem;
}
</style>
