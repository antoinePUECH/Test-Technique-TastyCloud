<template>
  <div>
    <NavBar/>
    <ProductList @add:product="addProduct"/>
  </div>
</template>

<script>
/* eslint-disable */
import NavBar from '@/components/NavBar.vue'
import ProductList from "@/components/ProductList";
export default {
  name: "Home",
  components: {
    NavBar,
    ProductList
  },
  methods: {
    addProduct(product) {
      console.log(product)
      this.$emit('add:product', product)
    }
  }
}
</script>

<style scoped>

</style>