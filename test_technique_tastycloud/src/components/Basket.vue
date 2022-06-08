<template>
  <TDropdown text="Mon panier" class="bg-blue-500 p-4 rounded-xl">
    <div v-for="product in getProductsBasket" :key="product.id" class="py-1 rounded-md shadow-xs">
      <div class="mt-4 flex justify-between">
        <div>
          <h3 class="text-sm text-gray-700">
            <a>
              <span aria-hidden="true" class="absolute inset-0" />
              {{ product.name }}
            </a>
          </h3>
          <p class="mt-1 text-sm text-gray-500">{{ product.color }}</p>
        </div>
        <p class="text-sm font-medium text-gray-900">{{ product.price }} €</p>
      </div>
    </div>
  </TDropdown>
</template>

<script>
/* eslint-disable */
import { TDropdown } from 'vue-tailwind/dist/components'
export default {
  name: "Basket",
  components: {
    TDropdown
  },
  computed: {
    getProductsBasket() {
      return this.$store.getters.getProductsBasket
    }
  }
}
</script>

<style scoped>

</style>