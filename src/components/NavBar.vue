<template>
  <ul>
    <li v-for="category in categories" :key="category">{{ category }}</li>
    <li @click="triggerShowAddCategory">+</li>
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