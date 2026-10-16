<script setup>
import { RouterLink, RouterView } from 'vue-router'
import vueLogo from './assets/vue.svg'
</script>

<template>
  <div class="studio">
    <header>
      <RouterLink class="brand" to="/" aria-label="Studio home">
        <img :src="vueLogo" width="28" height="28" alt="Vue" />
        <span>FIT5032 <span class="muted">/ Studio</span></span>
      </RouterLink>
      <nav aria-label="Main navigation">
        <RouterLink to="/">Home</RouterLink>
        <RouterLink to="/about">About</RouterLink>
      </nav>
    </header>
    <main><RouterView /></main>
    <footer><span>Internet applications development</span><span>Semester 2 / Week 12</span></footer>
  </div>
</template>
