<script setup>
import { computed, ref } from 'vue'

const initialPrice = ref()

const marja = ref(5)

const packingPrice = ref(150)

const serviceCommissionFixed = ref(425)
const serviceCommissionPercents = ref(7.4)

const chandaPercents = ref(2)

const wantedPrice = computed(() => initialPrice.value * (100 + marja.value) / 100)

// const serviceCommission = computed(() => {
//   return (
//       preResult.value / 100 * serviceCommissionPercents.value
//   ) + serviceCommissionFixed.value
// })

const result = computed(() => {
  return wantedPrice.value + packingPrice.value + serviceCommissionFixed.value +
      (wantedPrice.value * serviceCommissionPercents.value / 100) +
      (wantedPrice.value * chandaPercents.value / 100)
})
</script>

<template>

  <form>
    <div class="mb-3">
      <label for="initialPrice" class="form-label">Начальная сумма</label>
      <input type="number" class="form-control" id="initialPrice" v-model="initialPrice">
    </div>
    <div class="mb-3">
      <label for="marja" class="form-label">Маржа %</label>
      <input type="number" class="form-control" id="marja" v-model="marja">
    </div>
    <div class="mb-3">
      <label for="wantedPrice" class="form-label">Желамая сумма</label>
      <input type="number" readonly class="form-control" id="wantedPrice" v-model="wantedPrice">
    </div>
    <hr>
    <div class="mb-3">
      <label for="packingPrice" class="form-label">Упаковка товара</label>
      <input type="number" class="form-control" id="packingPrice" v-model="packingPrice">
    </div>
    <div class="mb-3">
      <label for="serviceCommissionPercents" class="form-label">Комиссия площадки %</label>
      <input type="number" class="form-control" id="serviceCommissionPercents" v-model="serviceCommissionPercents">
    </div>
    <div class="mb-3">
      <label for="serviceCommissionFixed" class="form-label">Комиссия площадки (фикс)</label>
      <input type="number" class="form-control" id="serviceCommissionFixed" v-model="serviceCommissionFixed">
    </div>
    <div class="mb-3">
      <label for="chanda" class="form-label">Неведомая комиссия %</label>
      <input type="number" class="form-control" id="chanda" v-model="chandaPercents">
    </div>
    <hr>
    <div class="mb-3">
      <label for="result" class="form-label">Цена на яндексе</label>
      <input type="number" readonly class="form-control" id="result" v-model="result">
    </div>
  </form>
</template>

<style scoped>
form {
  width: 400px;
  max-width: 100%;
}
.form-control {
  text-align: center;
}
</style>
