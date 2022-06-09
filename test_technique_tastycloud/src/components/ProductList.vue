<template>
  <div class="bg-white">
    <div class="max-w-2xl mx-auto py-16 px-4 sm:py-24 sm:px-6 lg:max-w-7xl lg:px-8">
      <h2 class="text-2xl font-medium tracking-tight text-gray-900">Tous les produits</h2>
      <div class="mt-6 grid grid-cols-1 gap-y-10 gap-x-6 sm:grid-cols-2 lg:grid-cols-4 xl:gap-x-8">
        <Product v-for="product in getProducts" :key="product.id" :description="product.description" :quantity="product.quantity" :id="product.id" :name="product.name" :price="product.price" :image-src="product.imageSrc" :image-alt="product.imageAlt" @product:click="sendProduct(product)" class="group relative cursor-pointer"/>
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
  props: {
    category: {
      type: String,
    }
  },
  computed: {
    getProducts() {
      if (!this.category) {
        return this.$store.getters.getAllProducts
      } else {
        return this.$store.getters.getProductsByCategory(this.category)
      }
    }
  },
  methods: {
    sendProduct(product) {
      this.$store.dispatch('addProductBasket', product.id)
    }
  }
}
</script>

<style scoped>

</style>