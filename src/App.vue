<script setup>
import { computed, onMounted, ref, watch } from 'vue'
import BarChart from './components/BarChart.vue'

const days = ['Ma', 'Di', 'Wo', 'Do', 'Vr', 'Za', 'Zo']
const steps = ref([0, 0, 0, 0, 0, 0, 0])

onMounted(() => {
  steps.value = [6200, 4100, 7800, 3500, 5200, 9100, 2800]
})

const total = computed(() => {
  let sum = 0
  for (let i = 0; i < steps.value.length; i++) {
    sum += steps.value[i] || 0
  }
  return sum
})

const avg = computed(() => Math.round(total.value / steps.value.length))

const belowGoal = computed(() => avg.value < 5000)

watch(belowGoal, (isBelow) => {
  console.log(isBelow ? 'Onder de 5000 stappen' : 'Doel gehaald!')
})
</script>

<template>
  <div class="card" :class="{ low: belowGoal }">
    <h1>Stappenteller</h1>

    <div class="days">
      <label v-for="(day, i) in days" :key="day">
        {{ day }}
        <input v-model.number="steps[i]" type="number" />
      </label>
    </div>

    <BarChart :labels="days" :values="steps" :color="belowGoal ? '#e0b400' : '#42b883'" />

    <p>Totaal: {{ total }} | Gemiddeld: {{ avg }} per dag</p>
  </div>
</template>

<style scoped>
:global(body) {
  background: white;
  font-family: sans-serif;
}

.card {
  max-width: 600px;
  margin: 40px auto;
  padding: 20px;
  border-radius: 12px;
  background: #e3f4ec;
}

.card.low {
  background: #fff3c4;
}

.days {
  display: grid;
  grid-template-columns: repeat(7, 1fr);
  gap: 6px;
  margin-bottom: 16px;
}

.days input {
  width: 100%;
  box-sizing: border-box;
}
</style>
