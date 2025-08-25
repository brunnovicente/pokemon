<script setup>
  import {RouterLink} from "vue-router";
</script>

<template>

  <nav class="navbar navbar-expand bg-body-tertiary">
    <div class="container-fluid">
      <div class="collapse navbar-collapse" id="navbarSupportedContent">
        <ul class="navbar-nav me-auto mb-2 mb-lg-0">
          <li class="nav-item">
            <RouterLink to="/" class="nav-link">1ª Geração</RouterLink>
          </li>
          <li class="nav-item">
            <RouterLink to="/geracao2" class="nav-link">2ª Geração</RouterLink>
          </li>
          <li class="nav-item">
            <RouterLink to="/geracao3" class="nav-link">3ª Geração</RouterLink>
          </li>
        </ul>
      </div>
    </div>
  </nav>

</template>

<style scoped>

</style>