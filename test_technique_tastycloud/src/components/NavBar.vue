<template>
  <div class="md:flex md:items-center md:justify-between p-4">
    <div class="flex-1 min-w-0">
      <h2 class="text-2xl font-bold leading-7 text-gray-900 sm:text-3xl sm:truncate">TastyCloud's Burgers</h2>
    </div>
    <div class="relative z-0 inline-flex rounded-md space-x-8">
      <Button text="Accueil" @button:click="goToHome"/>
      <Button text="Desserts" @button:click="goToDesserts"/>
      <Button text="Boissons" @button:click="goToDrinks"/>
    </div>
    <div class="mt-4 flex md:mt-0 md:ml-4">
      <Basket/>
    </div>
  </div>
</template>

<script>
import Basket from '@/components/Basket.vue'
import Button from '@/components/Button.vue'
export default {
  name: 'NavBar',
  components: {
    Basket,
    Button
  },
  methods: {
    goToHome() {
      this.$router.push('/')
    },
    goToDesserts() {
      this.$router.push('/desserts')
    },
    goToDrinks() {
      this.$router.push('/boissons')
    }
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
