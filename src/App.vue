<template>
  <main></main>
</template>

<script>
import Vue from 'vue'

import AddCategory from './components/AddCategory.vue'
import AddBill from './components/AddBill.vue'
import NavBar from './components/NavBar.vue'
import Chart from './components/Chart.vue'
import BillsTable from './components/BillsTable.vue'


export default {
  name: 'app',
  components: {
    AddCategory,
    AddBill,
    NavBar,
    Chart,
    BillsTable
  }
}

</script>

