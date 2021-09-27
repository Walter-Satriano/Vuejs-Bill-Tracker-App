<template>
  <ul class="list-reset inline flex justify-center border-b-4 mb-0">
    <li class="top_menu_items" v-for="category in categories" :key="category">{{ category }}</li>
    <li class="top_menu_items" @click="triggerShowAddCategory">+</li>
  </ul>
</template>

<script>
export default {
  methods: {
    triggerShowAddCategory() {
      this.$emit('triggerShowAddCategory')
    }
  },
  props: ['categories'],
}
</script>

<style lang="postcss" scoped>
.top_menu_items {
  @apply  p-4 inline bg-gray-200 hover:bg-gray-400 uppercase font-black cursor-pointer font-mono text-3xl;
}
</style>