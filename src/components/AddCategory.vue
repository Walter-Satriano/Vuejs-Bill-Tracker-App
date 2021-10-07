<template>
  <div class="flex items-center justify-center font-sans">
    <div class="w-full sm:w-3/5 lg:w-1/2 xl:w-2/5 border-2 border-green-500 rounded shadow p-6 m-4 text-center">
      <div class="font-bold">
        <h5 class="text-xl sm:text-2xl">Enter a category of bills</h5>
        <p class="text-base sm:text-lg">E.g. 'Electricity' or 'Gas' or 'Internet'</p>
        <div class="mt-7">
          <input
            class="w-full shadow border-2 border-green-500 rounded py-2 px-3 capitalize"
            placeholder="Add category"
            v-model="category"
          >
          <button
            class="add-bill-btn"
            @click="handleClick"
          >
            Add
          </button>
        </div>
      </div>
    </div>
  </div>
</template>

<script>

export default {
  name: 'AddCategory',
  data: function() {
    return {
      category: ''
    }
  },
  methods: {
    handleClick: function() {
      if(!this.category) {
        alert('Please enter a category')
        return
      }

      this.$emit('addCategory', this.category)
    },
  },
}
</script>

<style lang="postcss" scoped>
  .add-bill-btn {
    @apply rounded-full py-2 px-4 mt-5 bg-green-500 hover:bg-green-700
      text-white text-center font-bold text-lg sm:text-2xl
  }
</style>
