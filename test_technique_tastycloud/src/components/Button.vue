<template>
  <div @click="buttonClick" class="w96">
    <button class="inline-flex items-center p-2 border border-transparent rounded-lg shadow-sm text-white bg-indigo-600">
      {{ text }}
    </button>
  </div>
</template>

<script>
/* eslint-disable */
export default {
  name: "Button",
  props: {
    text: String
  },
  methods: {
    buttonClick() {
      console.log("Click")
      this.$emit('button:click')
    }
  }
}
</script>

<style scoped>

</style>