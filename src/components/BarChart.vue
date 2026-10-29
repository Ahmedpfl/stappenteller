<script setup>
import { computed } from 'vue'
import { Bar } from 'vue-chartjs'
import { Chart as ChartJS, BarElement, CategoryScale, LinearScale, Tooltip, Legend } from 'chart.js'

ChartJS.register(BarElement, CategoryScale, LinearScale, Tooltip, Legend)

const props = defineProps({
  values: { type: Array, required: true },
  labels: { type: Array, required: true },
  color: { type: String, default: '#42b883' }
})

const chartData = computed(() => ({
  labels: props.labels,
  datasets: [{ label: 'Stappen', data: props.values, backgroundColor: props.color }]
}))

const chartOptions = {
  responsive: true,
  plugins: { legend: { display: false } },
  scales: { y: { beginAtZero: true } }
}
</script>

<template>
  <Bar :data="chartData" :options="chartOptions" />
</template>
