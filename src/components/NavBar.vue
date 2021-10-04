<template>
  <ul class="list-reset sm:flex sm:flex-wrap justify-center mb-8 sm:py-4 lg:mb-12">

    <li
      class="top_menu_items"
      :class="[ activeCategory === '' ? 'bg-gray-600' : 'bg-gray-200' ]"
      @click="clearActiveCategory()"
    >All</li>

    <li
      class="top_menu_items"
      :class="[ activeCategory === category ? 'bg-gray-600' : 'bg-gray-200' ]"
      v-for="category in categories"
      :key="category"
      @click="setActiveCategory(category)"
    >{{ category }}</li>

    <li class="top_menu_items bg-gray-200" @click="triggerShowAddCategory">+</li>

  </ul>
</template>

<script>
export default {
  props: ['categories', 'activeCategory'],
  methods: {
    triggerShowAddCategory() {
      this.$emit('triggerShowAddCategory')
    },
    clearActiveCategory() {
      this.$emit('clearActiveCategory')
    },
    setActiveCategory(category) {
      this.$emit('setActiveCategory', category)
    }
  },
}
</script>

<style lang="postcss" scoped>
.top_menu_items {
  @apply  p-2 hover:bg-gray-400 uppercase font-black cursor-pointer font-mono text-base sm:text-2xl lg:text-4xl;
}
</style>