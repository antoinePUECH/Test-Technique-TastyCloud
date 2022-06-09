<template>
  <div>
    <NavBar/>
    <ProductList :category="category"/>
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
  props: {
    category: String
  },
}
</script>

<style scoped>

</style>