<template>
  <main>
    <AddCategory v-if="shouldShowAddCategory" v-on:addCategory="addCategory" />
    <div v-else>
      <NavBar />
      <div class="container flex">
        <div class="w-1/2">
          <BillsTable />
        </div>
        <div class="w-1/2">
          <Chart :bills="activeBills" />
        </div>
      </div>  
    </div>
  </main>
</template>

<script>
/* eslint-disable */
import AddCategory from './components/AddCategory.vue'
import AddBill from './components/AddBill.vue'
import NavBar from './components/NavBar.vue'
import Chart from './components/Chart.vue'
import BillsTable from './components/BillsTable.vue'


export default {
  name: 'App',
  data() {
    return {
      bills: [],
      categories: [],
      shouldShowAddCategory: true
    }
  },
  components: {
    AddCategory,
    AddBill,
    NavBar,
    Chart,
    BillsTable
  },
  methods: {
    addCategory(category) {
      this.categories.push(category)
      this.shouldShowAddCategory = false
    }
  },
  watch: {
    categories() {
      localStorage.setItem('categories', JSON.stringify(this.categories))
    }
  },
  mounted() {
    if (localStorage.getItem('categories')) {
      this.categories = JSON.parse(localStorage.getItem('categories'))
    }

    if (!this.categories.length) {
      this.shouldShowAddCategory = true
    }
    
  }
}

</script>

