<template>
  <!-- Header -->
  <header id="header">
    <h1>AmiiVue</h1>
    <nav id="nav">
      <ul>
        <li><RouterLink to="/" class="nav-link">Home</RouterLink></li>
        <li><RouterLink to="/list" class="nav-link">Liste Amiibo</RouterLink></li>
      </ul>
    </nav>
  </header>

  <!-- Banner -->
  <section id="banner">
    <header>
      <h2>Hey. Bienvenue sur ma collection</h2>
    </header>
  </section>
</template>

<script setup>
import { RouterLink } from 'vue-router'
</script>
