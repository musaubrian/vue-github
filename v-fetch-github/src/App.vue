<script setup>
import ViewJson from './components/ViewJson.vue';
import UploadJson from './components/UploadJson.vue';

</script>

<template>
  <main>
    <ViewJson/>
    <UploadJson/>
  </main>
</template>

<style>
  main {
    display: flex;
    flex-direction: column;
    flex-wrap: nowrap;
    justify-content: center;
    align-items: center;
    width: 100%;
    height: 100%;
    font-size: 1.2rem;
  }
</style>