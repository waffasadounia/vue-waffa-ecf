<template>
  <div id="page-wrapper" class="homepage is-preload">
    <section id="header">
      <h1>AmiiVue</h1>
      <nav id="nav">
        <ul>
          <li class="current"><RouterLink to="/">Home</RouterLink></li>
          <li><RouterLink to="/list">Liste Amiibo</RouterLink></li>
        </ul>
      </nav>
      <section id="banner">
        <header>
          <h2>Hey. Bienvenue sur ma collection</h2>
        </header>
      </section>
    </section>

    <section id="intro" class="container">
      <div class="row">
        <div class="col-4 col-12-medium" v-for="amiibo in randomAmiibos" :key="amiibo.tail">
          <section class="middle">
            <img :src="amiibo.image" />
            <header>
              <h2>{{ amiibo.character }}</h2>
            </header>
            <p>{{ amiibo.gameSeries }}</p>
          </section>
        </div>
      </div>
      <footer>
        <ul class="actions">
          <li><RouterLink to="/list" class="button large">Liste complète</RouterLink></li>
        </ul>
      </footer>
    </section>

    <section id="footer">
      <div class="container">
        <div class="row">
          <div class="col-12">
            <div id="copyright">
              <ul class="links">
                <li>&copy; AmiiVue ~ 2024</li><li>Design: <a href="http://html5up.net">HTML5 UP</a></li>
              </ul>
            </div>
          </div>
        </div>
      </div>
    </section>
  </div>
</template>

<script setup>
import { onMounted, ref } from 'vue'

const randomAmiibos = ref([])

onMounted(async () => {
  const response = await fetch('https://www.amiiboapi.com/api/amiibo/')
  const data = await response.json()
  const all = data.amiibo
  randomAmiibos.value = all.sort(() => 0.5 - Math.random()).slice(0, 3)
})
</script>
