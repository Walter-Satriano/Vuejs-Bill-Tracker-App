<script>
  import { Bar } from 'vue-chartjs';
  import moment from 'moment';


  /* months is the list of month names, and based on the current month,
  which we determine from the current date, I fill the orderedMonths array, and I return it */
  const last12Months = () => {
    const months = [
      'January',
      'February',
      'March',
      'April',
      'May',
      'June',
      'July',
      'August',
      'September',
      'October',
      'November',
      'December',
    ]

    const today = new Date()
    const orderedMonths = []
    let month = today.getMonth() + 1
    
    if (month === 12) month = 0  //correctly handle december

    for (let i = 0; i < 12; i++) {
      orderedMonths.push(months[month])
      month === 11 ? (month = 0) : month++
    }

    return orderedMonths
  }

  /* This function accepts an array of bills, filters out bills older than 1 year,
  and returns the total amount we paid each month */
  const processBills = (bills) => {
    const oneYearAgo = moment().subtract(1, 'years')
    const months = last12Months()
    const monthsWithValues = new Array(12).fill(0)

    for (const month of monthsWithValues) {
      monthsWithValues[month] = 0
    }

    for (const bill of bills) {
      if (moment(bill.date).isSameOrBefore(oneYearAgo)) {
        continue
      }
      const monthName = moment(bill.date).format('MMMM')
      const indexOfMonth = months.indexOf(monthName)
      monthsWithValues[indexOfMonth] += parseInt(bill.amount)
    }

    return monthsWithValues
  }


  /* The component extends the Bar component we imported from vue-chartjs at the beginning of this lesson,
  and this is why there is no template part in this component: everything is handled for us. 
  We just need to call the renderChart method of the Bar component. We do so in the mounted and in the bills watcher,
  so the chart is re-rendered when the component mounts, and when the bills change.
  We abstract that in the displayChart method. We pass in the labels, using the last12Months() function we defined above,
  and also the months’ data, using processBills(). */
  
  export default {
    extends: Bar,
    props: ['bills'],
    methods: {
      displayChart: function () {
        this.renderChart({
          labels: last12Months(),
          datasets: [
            {
              label: 'Amount',
              backgroundColor: 'lightgreen',
              data: processBills(this.bills),
            },
          ],
        }, {responsive: true, maintainAspectRatio: true})
      },
    },
    mounted: function () {
      this.displayChart()
    },
    watch: {
      bills: function () {
        this.displayChart()
      },
    },
  }
</script>
