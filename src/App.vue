<script setup lang="ts">
  import HelloWorld from './components/HelloWorld.vue';
  import OptionsApiComponent from './components/OptionsApiComponent.vue';
  import CompositionApiComponent from './components/CompositionApiComponent.vue';
</script>


<template>
  <HelloWorld msg="Vite + Vue" />
  <OptionsApiComponent />
  <!-- <CompositionApiComponent :active="true" /> --> <!-- TEM QUE TER O : PARA O VUE IDENTIFICAR QUE ELE TEM QUE INTERPRETAR O VALOR CONTIDO DENTRO DAS ASPAS -->
  <CompositionApiComponent active :prop-message="'mensagem passada por prop'" />
</template>


<style>
  html{
    background-color: darkgray;
  }
</style>
