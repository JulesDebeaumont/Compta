<script setup lang="ts">
import { ref } from 'vue';

// refs
const defaultPrice = ref<number | null>(null)
const priceWithTVA = ref<number | null>(null)
const priceWithMarge = ref<number | null>(null)
const priceWithMargeAndTVA = ref<number | null>(null)
const priceClient = ref<number | null>(null)
const marge = ref(30)
const tva = ref(20)

// functions
function updatePrices(value: number | null) {
  if (value != null) {
    defaultPrice.value = value
    priceWithTVA.value = Math.round((defaultPrice.value * (1 + (tva.value / 100))) * 100) / 100
    priceWithMarge.value = Math.round((defaultPrice.value * (1 + (marge.value / 100))) * 100) / 100
    priceWithMargeAndTVA.value = Math.round(((defaultPrice.value * (1 + (tva.value / 100))) * (1 + (marge.value / 100))) * 100) / 100
    priceClient.value = Math.ceil(priceWithMargeAndTVA.value / 5) * 5
  }
}
</script>

<template>
  <q-page class="column items-center justify-evenly">
    <div class="q-gutter-y-md q-px-sm q-py-md column" style="min-width: 300px">
      <q-input type="number" dark v-model="tva" color="secondary" label="TVA" @update:model-value="(value: number | null) =>
      updatePrices(value)" suffix="%" />
        <q-input type="number" dark v-model="marge" color="secondary" label="Marge"
          @update:model-value="(value: number | null) => updatePrices(value)" suffix="%" class="q-pb-xl" />

        <q-input type="number" dark v-model="defaultPrice" color="secondary" label="Prix"
          @update:model-value="(value: number | null) => updatePrices(value)" suffix="€" class="q-pt-xl" />
        <q-input disable dark v-model="priceWithTVA" color="secondary" label="Prix (TVA)" suffix="€" />
        <q-input disable dark v-model="priceWithMarge" color="secondary" label="Prix avec marge" suffix="€" />
        <q-input disable dark v-model="priceWithMargeAndTVA" color="secondary" label="Prix avec marge (TVA)" suffix="€"
          class="q-pb-xl" />
        <q-input disable dark v-model="priceClient" color="secondary" label="Prix client" suffix="€" class="q-pt-xl" />
    </div>
  </q-page>
</template>

<style>
input[type="number"]::-webkit-outer-spin-button,
  input[type="number"]::-webkit-inner-spin-button {
    -webkit-appearance: none;
    margin: 0;
  }
</style>
