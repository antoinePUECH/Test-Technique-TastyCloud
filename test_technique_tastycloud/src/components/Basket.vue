<template>
  <div class="text-center" data-app>
    <v-menu offset-y min-width="200" :close-on-content-click="false">
      <template v-slot:activator="{ on }">
          <v-btn
              color="primary"
              dark
              v-on="on"
          >
            Mon panier
          </v-btn>
        <span class="inline-flex items-center px-2.5 py-0.5 rounded-full text-xs font-medium bg-blue-100 text-blue-800 absolute right-1 top-2">
          {{  getTotalQuantity }}
        </span>
      </template>
      <v-list v-if="getProductsBasket.length >= 1">
        <v-list-item-content
            v-for="product in getProductsBasket"
            :key="product.id"
        >
          <div class="flex justify-around">
            <p class="text-base font-medium">{{ product.name }}</p>
            <p class="text-base font-medium">{{ product.price * product.quantity }} €</p>
          </div>
          <div class="flex justify-around">
            <div class="flex align-center">
              <Button text="-" @button:click="decrementQuantity(product)"/>
              <p class="text-base font-medium px-2">{{ product.quantity }}</p>
              <Button text="+" @button:click="incrementQuantity(product)"/>
            </div>
          </div>
        </v-list-item-content>
        <p class="text-lg font-bold">Total :{{ getTotalPrice }} €</p>
      </v-list>
      <v-list v-else>
        <v-list-item-content>
          <p class="text-lg font-bold">Votre panier est vide</p>
        </v-list-item-content>
      </v-list>
    </v-menu>
  </div>
</template>

<script>
/* eslint-disable */
import { TDropdown } from 'vue-tailwind/dist/components'
import Button from '@/components/Button'
export default {
  name: "Basket",
  components: {
    TDropdown,
    Button
  },
  data() {
    return {
      totalPrice: 0,
    }
  },
  computed: {
    getProductsBasket() {
      return this.$store.getters.getProductsBasket
    },
    getTotalPrice() {
      const products = this.getProductsBasket
      return products.reduce((total, product) => {
        return total + product.price * product.quantity
      }, 0)
    },
    getTotalQuantity() {
      const products = this.getProductsBasket
      return products.reduce((total, product) => {
        return total + product.quantity
      }, 0)
    }
  },
  methods: {
    decrementQuantity(product) {
      this.$store.dispatch('decrementQuantity', product.id)
    },
    incrementQuantity(product) {
      this.$store.dispatch('incrementQuantity', product.id)
    }
  }
}
</script>

<style scoped>

</style>