<script setup lang="ts">
  import HelloWorld from './components/HelloWorld.vue';
  import OptionsApiComponent from './components/OptionsApiComponent.vue';
  import CompositionApiComponent from './components/CompositionApiComponent.vue';
</script>


<template>
  <HelloWorld msg="Vite + Vue" />
  <OptionsApiComponent />
  <CompositionApiComponent />
</template>


<style>
  html{
    background-color: darkgray;
  }
</style>
