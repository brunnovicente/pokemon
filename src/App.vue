<script setup>
  import {RouterView } from 'vue-router'
  import 'bootstrap/dist/css/bootstrap.min.css'
  import 'bootstrap/dist/js/bootstrap.bundle.js'
  import Barra from './componentes/Barra.vue'
</script>

<template>

  <Barra />

  <RouterView />
</template>