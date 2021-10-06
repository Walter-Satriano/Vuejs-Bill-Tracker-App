<template>
  <div class="mb-8 lg:mb-0 font-sans">
    <table class="table mx-auto w-5/6 text-base sm:text-lg">
      <thead class="bg-blue-400 text-white">
        <tr>
          <th scope="col">Date</th>
          <th scope="col">Amount</th>
          <th scope="col">Category</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="(bill, index) in bills" :key="index">
          <td>{{ bill.date | moment("MMM D YYYY")}}</td>
          <td>{{ bill.amount }} €</td>
          <td>{{ bill.category }}</td>
          <td class="border-none" >
            <button class="remove-bill-btn" @click="removeBill(index)">
              <font-awesome-icon icon="trash"/>
            </button>
          </td>
        </tr>
      </tbody>
    </table>

    <button class="add-bill-btn" @click="triggerShowAddBill">Add New Bill</button>
  </div>
</template>

<script>
  export default {
    name: 'BillsTable',
    methods: {
      triggerShowAddBill: function() {
        this.$emit('triggerShowAddBill')
      },

      removeBill: function(index) {
        this.$emit('removeBill', index)
      }
    },
    props: ['bills']
  }
</script>

<style lang="postcss" scoped>
  th, td {
    @apply border-2 border-black
  }

  td, th {
    @apply py-1
  }

  .add-bill-btn {
    @apply rounded-full py-2 px-4 mt-4 bg-blue-500 hover:bg-blue-700
      text-white text-center font-bold text-lg sm:text-2xl
  }

  .remove-bill-btn {
    @apply rounded-full h-8 w-8 bg-red-600 text-white text-center font-bold
  }
</style>