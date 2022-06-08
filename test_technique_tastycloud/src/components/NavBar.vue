<template>
  <div class="md:flex md:items-center md:justify-between m-5">
    <div class="flex-1 min-w-0">
      <h2 class="text-2xl font-bold leading-7 text-gray-900 sm:text-3xl sm:truncate">Back End Developer</h2>
    </div>
    <div class="mt-4 flex md:mt-0 md:ml-4">
      <Basket/>
    </div>
  </div>
</template>

<script>
import Basket from '@/components/Basket.vue'
export default {
  name: 'NavBar',
  components: {
    Basket
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
