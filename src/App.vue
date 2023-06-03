<script setup>
import CalculatorForm from "./components/CalculatorForm.vue"
import { ref } from 'vue'

const currentTab = ref('fiat')
const initialUsdt = ref()
</script>

<template>
  <ul class="nav nav-tabs mb-3">
    <li class="nav-item">
      <a
          class="nav-link"
          :class="{'active': currentTab === 'fiat'}"
          href="#"
          v-text="'Безнал'"
          @click.prevent="currentTab = 'fiat'"
      />
    </li>
    <li class="nav-item">
      <a
          class="nav-link"
          :class="{'active': currentTab === 'usdt'}"
          href="#"
          v-text="'USDT'"
          @click.prevent="currentTab = 'usdt'"
      />
    </li>
  </ul>
  <CalculatorForm
      v-show="currentTab === 'fiat'"
      @initial-price-change="initialUsdt = $event"
  />
  <CalculatorForm
      v-show="currentTab === 'usdt'"
      :initial="initialUsdt"
  />
</template>

<style scoped>
.nav-tabs {
  width: 100% ;
}
</style>
