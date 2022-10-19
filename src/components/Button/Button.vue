<template>
  <button @click="$emit('click')"><slot></slot></button>
</template>
<script setup lang="ts"></script>
<style lang="css">
@import "./button-style.css";
</style>
