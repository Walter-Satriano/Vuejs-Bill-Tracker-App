<template>
  <main>
    <NavBar />
    <div class="container flex">
      <div class="w-1/2">
        <BillsTable />
      </div>
      <div class="w-1/2">
        <Chart :bills="activeBills" />
      </div>
    </div>  
  </main>
</template>

<script>

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

