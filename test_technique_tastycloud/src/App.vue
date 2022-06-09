<template>
  <div id="app">
    <router-view/>
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
        name: 'Saint Louis',
        imageSrc: 'https://images.rtl.fr/~c/770v513/rtl/www/1460953-un-hamburger-image-d-illustration.jpg',
        imageAlt: "Burger",
        price: 17.5,
        category: 'burger',
        quantity: 1,
        description: 'Pain maison, tomates, salade, ketchup, cheddar, steak (180g), oignons caramélisés, moutarde au miel',
        inBasket: false
      },
      {
        id: 2,
        name: 'Double Cloud Bacon',
        imageSrc: 'https://offloadmedia.feverup.com/parissecret.com/wp-content/uploads/2020/07/19141709/Copie-de-Design-sans-titre-13.jpg',
        imageAlt: "Burger",
        price: 22,
        category: 'burger',
        quantity: 1,
        description: 'Pain maison, cornichons, bacon, cheddar, steak (150g) x2, ketchup',
        inBasket: false
      },
      {
        id: 3,
        name: 'Double chicken tasty',
        imageSrc: 'https://fr.openfoodfacts.org/images/products/200/000/011/6553/front_fr.4.full.jpg',
        imageAlt: "Burger",
        price: 23.5,
        category: 'burger',
        quantity: 1,
        description: 'Pain maison, salade, sauce au poivre, tenders de poulet (150g) x2, bacon, cheddar',
        inBasket: false
      },
      {
        id: 4,
        name: 'Tiramisu',
        imageSrc: 'https://www.finedininglovers.fr/sites/g/files/xknfdk1291/files/styles/recipes_1200_800_fallback/public/fdl_content_import_scripts/Original_4306_recette-tiramisu-maxime-frederic-le-george_0.jpg?itok=gRn4oU4s',
        imageAlt: "Tiramisu",
        price: 6,
        category: 'dessert',
        quantity: 1,
        description: 'Sucre, beurre, farine, sucre de canne, lait, oeuf, caféine, vanille',
        inBasket: false
      },
      {
        id: 5,
        name: 'Île flottante',
        imageSrc: 'https://img.cuisineaz.com/660x660/2013/12/20/i107516-ile-flottante-au-caramel.jpeg',
        imageAlt: "Île flottante",
        price: 7.5,
        category: 'dessert',
        quantity: 1,
        description: 'Oeufs, sucre, caramel',
        inBasket: false
      },
      {
        id: 6,
        name: 'Cupcake fraise coco',
        imageSrc: 'https://res.cloudinary.com/hv9ssmzrz/image/fetch/c_fill,f_auto,h_600,q_auto,w_800/https://s3-eu-west-1.amazonaws.com/images-ca-1-0-1-eu/recipe_photos/original/101738/Muffins-aux-Bananes-Fraises-Noix-de-Coco-et-Gruau.jpg',
        imageAlt: "Cupcake",
        price: 3,
        category: 'dessert',
        quantity: 1,
        description: 'Fraise, noix de coco, beurre, farine, sucre, oeuf, caféine',
        inBasket: false
      },
      {
        id: 7,
        name: 'Diabolo fraise',
        imageSrc: 'https://assets.afcdn.com/recipe/20210308/118427_w1024h768c1cx1061cy706.jpg',
        imageAlt: "Diabolo",
        price: 5,
        category: 'boisson',
        quantity: 1,
        description: 'Sirop de fraise, limonade, menthe',
        inBasket: false
      },
      {
        id: 8,
        name: 'Blue laggon',
        imageSrc: 'https://assets.afcdn.com/recipe/20190222/88138_w1024h1024c1cx1762cy2643.webp',
        imageAlt: "Blue laggon",
        price: 5,
        category: 'boisson',
        quantity: 1,
        description: 'Curaçao, vodka, jus de citron, citron vert',
        inBasket: false
      },
    ]
  },
  getters: {
    getAllProducts: state => {
      return state.products
    },
    getProductsBasket: state => {
      return state.products.filter(product => product.inBasket)
    },
    getProductById: (state) => (id) => {
      return state.products.find(product => product.id === id)
    },
    getProductsByCategory: (state) => (category) => {
      return state.products.filter(product => product.category === category)
    }
  },
  mutations: {
    addProductBasket(state, id) {
      const product = state.products.find(product => product.id === id)
      product.inBasket = true
    },
    incrementQuantity(state, id) {
      const product = state.products.find(product => product.id === id)
      product.quantity++
    },
    decrementQuantity(state, id) {
      const product = state.products.find(product => product.id === id)
      if (product.quantity > 1) {
        product.quantity--
      } else {
        if (window.confirm(`Êtes-vous sur de vouloir retirer ${product.name} du panier ?`)) {
          product.inBasket = false
        }
      }
    },
  },
  actions: {
    addProductBasket: ({commit}, id) => {
      commit('addProductBasket', id)
    },
    incrementQuantity: ({commit}, id) => {
      commit('incrementQuantity', id)
    },
    decrementQuantity: ({commit}, id) => {
      commit('decrementQuantity', id)
    }
  }
})
// @ is an alias to /src

export default {
  name: 'HomeView',
  store: store,
}
</script>

<style src="./assets/tailwind.css"/>
