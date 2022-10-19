<template>
  <div class="ProgressBar">
    <h2><slot></slot></h2>
    <div class="ProgressBar_flex">
      <p>{{ rawHtmlValue }}</p>
      <div class="ProgressBar_container">
        <span :class="currentState" :style="{ ...widthValue }"></span>
      </div>
    </div>
  </div>
</template>
<script setup lang="ts">
import { ref, computed } from "vue";
export interface Props {
  progressionValue: number;
}
const props = withDefaults(defineProps<Props>(), {
  progressionValue: 0,
});

const rawHtmlValue = computed(() => {
  if (props.progressionValue > 100) {
    return "100%";
  }
  if (props.progressionValue < 0) {
    return "0%";
  }
  return `${props.progressionValue}%`;
});
const widthValue = computed(() => {
  if (props.progressionValue > 100) {
    return { width: `100%` };
  }
  if (props.progressionValue < 0) {
    return { width: `0` };
  }
  return { width: `${props.progressionValue}%` };
});
const currentState = computed(() => {
  if (props.progressionValue < 25) {
    return "ProgressBar_0-to-25";
  }
  if (props.progressionValue >= 25 && props.progressionValue < 50) {
    return "ProgressBar_25-to-50";
  }
  if (props.progressionValue >= 50 && props.progressionValue < 75) {
    return "ProgressBar_50-to-75";
  }
  //   if (props.progressionValue < 25){
  return "ProgressBar_75-to-100";
  //   }
});
</script>
<style lang="css">
@import "./progressbar-style.css";
</style>
