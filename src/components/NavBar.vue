<template>
  <div class="font-sans text-center mb-12 sm:mb-24">
    <ul class="list-reset sm:flex sm:flex-wrap justify-center sm:py-4">
      <li
        class="top_menu_items"
        :class="[ activeCategory === '' ? 'bg-green-700' : 'bg-green-400' ]"
        @click="clearActiveCategory()"
      >All</li>

      <li
        class="top_menu_items"
        :class="[ activeCategory === category ? 'bg-green-700' : 'bg-green-400' ]"
        v-for="category in categories"
        :key="category"
        @click="setActiveCategory(category)"
      >{{ category }}</li>
    </ul>
    <button class="add-category-btn" @click="triggerShowAddCategory">Add New Category</button>
  </div>
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
  @apply p-2 border-b-2 rounded-lg sm:border-0 sm:mx-2 sm:my-2
    hover:bg-green-500 uppercase font-bold cursor-pointer
    text-lg text-white text-center sm:text-2xl lg:text-3xl;
}
.add-category-btn {
  @apply rounded-full py-2 px-4 mt-4 bg-green-500 hover:bg-green-700
    text-white text-center font-bold text-lg sm:text-2xl
}
</style>