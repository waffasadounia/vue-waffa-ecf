<template>
  <div id="page-wrapper" class="left-sidebar is-preload">
    <section id="header">
      <h1>Détail</h1>
      <nav id="nav">
        <ul>
          <li><RouterLink to="/">Home</RouterLink></li>
          <li><RouterLink to="/list">Liste Amiibo</RouterLink></li>
        </ul>
      </nav>
    </section>

    <section id="main">
      <div class="container">
        <div class="row">
          <div class="col-4 col-12-medium">
            <section class="box" v-if="amiibo">
              <header><h3>Infos</h3></header>
              <p>
                amiiboSeries: <b>{{ amiibo.amiiboSeries }}</b><br />
                Personnage: {{ amiibo.character }}<br />
                Série de jeux: {{ amiibo.gameSeries }}<br />
                type: {{ amiibo.type }}
              </p>
            </section>

            <section class="box" v-if="amiibo">
              <header><h3>Dates de sortie</h3></header>
              <ul class="divided">
                <li>australie: {{ amiibo.release.au }}</li>
                <li>europe: {{ amiibo.release.eu }}</li>
                <li>japonp: {{ amiibo.release.jp }}</li>
                <li>usa: {{ amiibo.release.na }}</li>
              </ul>
            </section>
          </div>

          <div class="col-8 col-12-medium imp-medium">
            <article class="box post" v-if="amiibo">
              <img :src="amiibo.image" class="featured" />
              <header>
                <h2>{{ amiibo.name }}</h2>
                <p>{{ amiibo.type }}</p>
              </header>
            </article>
          </div>
        </div>
      </div>
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
import { useRoute } from 'vue-router'

const route = useRoute()
const amiibo = ref(null)

onMounted(async () => {
  const tail = route.params.tail
  const response = await fetch(`https://www.amiiboapi.com/api/amiibo/?tail=${tail}`)
  const data = await response.json()
  amiibo.value = data.amiibo[0]
})
</script>
