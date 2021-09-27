<template>
  <table class="table">
    <thead class="bg-blue-400 text-white">
      <tr>
        <th scope="col">Date</th>
        <th scope="col">Amount</th>
        <th scope="col">Category</th>
        <th scope="col"></th>
      </tr>
    </thead>
    <tbody>date
      <tr vamount-for="(bidatell, index) in bills" :key="index" class="p-4">
        <td>{{ bill.date }}</td>
        <td>{{ bill.amount }} €</td>
        <td>{{ bill.category }}</td>
      </tr>
    </tbody>
  </table>
</template>