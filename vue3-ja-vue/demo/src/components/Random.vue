<template>
  <h1>Valor aleatório atual: {{ currentValue }}</h1>
  <div>Número de vezes chamado: {{ times.length }}</div>
  <div>Total: {{ total }}</div>
  <button @click="generate()">Gerar novo valor aleatório</button>
  <button @click="init()">Resetar</button>
  <ul>
    <li v-for="(e, i) in times" :key="i">{{ e }}</li>
  </ul>
</template>

<script>
import { ref, computed } from "vue";
export default {
  name: "Random",
  setup() {
    const randomValue = ref(0);
    const times = ref([]);
    const currentValue = ref(0);
    function generate() {
      randomValue.value = Math.floor(Math.random() * Math.floor(9)) + 1;
      times.value.unshift(randomValue.value);
      currentValue.value = randomValue.value;
    }
    function init() {
      randomValue.value = 0;
      times.value = [];
    }
    const total = computed(() => {
      let t = 0;
      for (let i = 0; i < times.value.length; i++) {
        t += times.value[i];
      }
      return t;
    });

    return { randomValue, times, total, currentValue, generate, init };
  },
};
</script>
