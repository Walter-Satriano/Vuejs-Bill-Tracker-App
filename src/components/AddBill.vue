<template>
  <div>
    <h1>Enter a new bill</h1>
    <p></p>
    <div>
      <select v-model="category">
        <option v-for="category in categories" :value="category" :key="category">
          {{ category }}
        </option>
      </select>
      <datepicker v-model="date"></datepicker>
      <input placeholder="Set amount" v-model="amount">
      <button @click="handleClick">Add</button>
    </div>
  </div>
</template>

<script>
  import Datepicker from 'vuejs-datepicker'

  export default {
    name: 'AddBill',
    data: function () {
      return {
        date: new Date(),
        category: this.categories[0],
        amount: 0,
      }
    },
    components: {
      Datepicker,
    },
    methods: {
      handleClick: function() {
        if (!this.date) {
          alert("Please, enter a date!")
          return
        }
        if (!this.amount) {
          alert("Please, enter an amount!")
          return
        }

        this.$emit('addBill', {
          date: this.date,
          category: this.category,
          amount: parseInt(this.amount, 10)
        })
      }
    },
    props: ['categories'],
  }
</script>