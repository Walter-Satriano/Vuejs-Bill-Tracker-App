<template>
  <div class="flex items-center justify-center font-sans">
    <div class="w-full sm:w-3/5 lg:w-1/2 xl:w-2/5 border-2 border-blue-500 rounded shadow p-6 m-4 text-center">
      <div class="font-bold">
        <h5 class="text-xl sm:text-2xl">Enter a new bill</h5>
        <div class="text-base sm:text-lg mt-7">
          <p class="text-left mb-1">Select a date:</p>
          <datepicker
            wrapper-class="shadow border-2 border-blue-500 rounded"
            input-class="w-full py-2 px-3"
            v-model="date"
          ></datepicker>

          <p class="text-left mb-1 mt-5">Select a date:</p>
          <select v-model="category" class="w-full shadow border-2 border-blue-500 rounded py-2 px-3">
            <option v-for="category in categories" :value="category" :key="category">{{ category }}</option>
          </select>

          <p class="text-left mb-1 mt-5">Set an amount:</p>
          <input
            class="w-full shadow border-2 border-blue-500 rounded py-2 px-3"
            v-model="amount"
          >
          <button
            class="add-bill-btn"
            @click="handleClick"
          >Add</button>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import Datepicker from "vuejs-datepicker";

export default {
  name: "AddBill",
  props: ["categories"],
  data: function() {
    return {
      date: new Date(),
      category: this.categories[0],
      amount: 0
    };
  },
  components: {
    Datepicker
  },
  methods: {
    handleClick: function() {
      if (!this.date) {
        alert("Enter a date");
        return;
      }
      if (!this.amount) {
        alert("Enter an amount");
        return;
      }

      this.$emit("addBill", {
        date: this.date,
        category: this.category,
        amount: parseInt(this.amount, 10)
      });
    },
  }
};
</script>

<style lang="postcss" scoped>
  .add-bill-btn {
    @apply rounded-full py-2 px-4 mt-5 bg-blue-500 hover:bg-blue-700
      text-white text-center font-bold text-lg sm:text-2xl
  }
</style>
