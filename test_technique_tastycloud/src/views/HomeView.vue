<template>
  <div class="home">
    <Home/>
  </div>
</template>

<script>
import Vue from 'vue'
import Vuex from 'vuex'
Vue.use(Vuex)
const store = new Vuex.Store({
  state: {
    products: [
      {
        id: 1,
        name: 'Basic Tee',
        imageSrc: 'https://tailwindui.com/img/ecommerce-images/product-page-01-related-product-01.jpg',
        imageAlt: "Front of men's Basic Tee in black.",
        price: 35,
        color: 'Black',
        inBasket: true
      },
      {
        id: 2,
        name: 'Bottle',
        imageSrc: 'https://tailwindui.com/img/ecommerce-images/category-page-04-image-card-01.jpg',
        imageAlt: "Front of men's Basic Tee in black.",
        price: 35,
        color: 'Black',
        inBasket: false
      },
    ]
  },
  getters: {
    getProduct: state => {
      return state.products
    },
    getProductsBasket: state => {
      return state.products.filter(product => product.inBasket)
    },
    getProductById: (state) => (id) => {
      return state.products.find(product => product.id === id)
    }
  },
  mutations: {
    addProductBasket(state, id) {
      const product = state.products.find(product => product.id === id)
      product.inBasket = true
    }
  },
  actions: {
    addProductBasket: ({commit}, id) => {
      commit('addProductBasket', id)
    }
  }
})
// @ is an alias to /src
import Home from '@/components/Home.vue'

export default {
  name: 'HomeView',
  store: store,
  components: {
    Home
  }
}
</script>
