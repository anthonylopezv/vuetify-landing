<template>
  <v-container>
    <h1>CORONAVIRUS PERÚ</h1>

    <v-row>
      <v-col cols="12">
        <SalesGraph 
          :cases="cases"
          :deaths="deaths"
          :initDate="initDate"
          :finishDate="finishDate"
        />
      </v-col>
    </v-row>

    <v-row>
      <v-col
        cols="12"
        md="6"
        lg="3" 
        v-for="statistic in statistics"
        :key="`${statistic.title}`"
      >
        <StatisticCard :statistic="statistic"/>
      </v-col>
      
    </v-row>
    
    <v-row>
      <v-col cols="12">
        <EmployeesTable :employees="employees" @select-employee="setEmployee" />
      </v-col>
      <!-- <v-col cols="4" md="4">
        <EventTimeline :timeline="timeline" />
      </v-col> -->
    </v-row>
  
    <v-snackbar v-model="snackbar" :left="$vuetify.breakpoint.lgAndUp">
      You have selected {{ selectedEmployee.name }},
      {{ selectedEmployee.title }}
      <v-btn color="pink" text @click="snackbar = false">
        Close
      </v-btn>
    </v-snackbar>
  </v-container>
</template>

<script>
import moment from "moment";

import EmployeesTable from '../components/EmployeesTable'
import SalesGraph from '../components/SalesGraph'
import StatisticCard from '../components/StatisticCard'

import employeesData from '../data/employees.json'
import salesData from '../data/sales.json'
import statisticsData from '../data/statistics.json'

export default {
  async asyncData({ $axios }) {
    const { data } = await $axios.get('https://api.covid19api.com/live/country/peru/status/confirmed')

    const cases = data.map(c => c.Confirmed)
    const deaths = data.map(d => d.Deaths)

    const dates = data.map((date) => moment(date.Date).format("DD/MM/YYYY"))
    const initDate = dates[0]
    const finishDate = dates[dates.length - 1]

    return { cases, deaths, initDate, finishDate }
  },
  components: {
    EmployeesTable,
    SalesGraph,
    StatisticCard
  },
  data() {
    return {
      employees: employeesData,
      sales: salesData,
      selectedEmployee: {
        name: '',
        title: ''
      },
      snackbar: false,
      statistics: statisticsData
    }
  },
  methods: {
    setEmployee(event) {
      this.snackbar = true
      this.selectedEmployee.name = event.name
      this.selectedEmployee.title = event.title
    }
  }
}
</script>