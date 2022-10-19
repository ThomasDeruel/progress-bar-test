<script setup lang="ts">
import { ref } from "vue";
import Button from "./components/Button/Button.vue";
import ProgressBar from "./components/ProgressBar/ProgressBar.vue";

const progressBarList = ref([
  {
    text: "Initialisation du test technique",
    value: 0,
  },
  { text: "Avancement de la phase de développement", value: 50 },
]);

const resetValue = () => {
  progressBarList.value = progressBarList.value.map((el) => {
    return { ...el, value: 0 };
  });
};

const Add5percent = () => {
  progressBarList.value = progressBarList.value.map((el) => {
    return { ...el, value: el.value + 5 };
  });
};

const Add10percent = () => {
  progressBarList.value = progressBarList.value.map((el) => {
    return { ...el, value: el.value + 10 };
  });
};
</script>

<template>
  <h1>Deruel, Thomas: réalisation le 19/10/2022</h1>
  <div v-for="(pb, index) in progressBarList" :key="index">
    <ProgressBar :progressionValue="pb.value">{{ pb.text }} </ProgressBar>
  </div>
  <div class="actions">
    <Button @click="resetValue">Remettre à zéro les compteurs</Button>
    <Button @click="Add5percent">Ajouter 5%</Button>
    <Button @click="Add10percent">Ajouter 10%</Button>
  </div>
</template>

<style scoped>
h1 {
  margin-bottom: 24px;
}
.actions {
  margin-top: 24px;
  display: flex;
  gap: 1rem;
  justify-content: center;
}
</style>
