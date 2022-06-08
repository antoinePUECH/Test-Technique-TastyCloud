<template>
  <div class="bg-white">
    <div class="max-w-2xl mx-auto py-16 px-4 sm:py-24 sm:px-6 lg:max-w-7xl lg:px-8">
      <h2 class="text-2xl font-medium tracking-tight text-gray-900">Produit disponible</h2>
      <div class="mt-6 grid grid-cols-1 gap-y-10 gap-x-6 sm:grid-cols-2 lg:grid-cols-4 xl:gap-x-8">
        <Product v-for="product in getProducts" :key="product.id" :color="product.color" :name="product.name" :price="product.price" :image-src="product.imageSrc" :image-alt="product.imageAlt" @product:click="sendProduct(product)" class="group relative"/>
      </div>
    </div>
  </div>
</template>

<script>
import Product from './Product.vue'
export default {
  components: {
    Product
  },

  name: "ProductList",
  computed: {
    getProducts() {
      return this.$store.getters.getProduct
    }
  },
  methods: {
    sendProduct(product) {
      console.log(product)
      this.$store.dispatch('addProductBasket', product.id)
      console.log(this.$store.getters.getProductsBasket)
    }
  }
}
</script>

<style scoped>

</style>