<template>
  <div id="page-wrapper" class="no-sidebar is-preload">
    <section id="header">
      <h1>Liste</h1>
      <nav id="nav">
        <ul>
          <li><RouterLink to="/">Home</RouterLink></li>
          <li class="current"><RouterLink to="/list">Liste Amiibo</RouterLink></li>
        </ul>
      </nav>
    </section>

    <section id="main">
      <div class="container">
        <article class="box post">
          <header>
            <h2>Ma Collection (10 par 10)</h2>
            <p>Page {{ page }}</p>
          </header>
          <table>
            <tr>
              <th>Character</th>
              <th>Game Series</th>
              <th>Action</th>
            </tr>
            <tr v-for="item in paginated" :key="item.tail">
              <td>{{ item.character }}</td>
              <td>{{ item.gameSeries }}</td>
              <td>
                <RouterLink :to="`/detail/${item.tail}`">
                  <button>voir</button>
                </RouterLink>
              </td>
            </tr>
          </table>
          <button @click="nextPage">Charger plus</button>
        </article>
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
import { onMounted, ref, computed } from 'vue'

const amiibos = ref([])
const page = ref(1)
const perPage = 10

onMounted(async () => {
  const response = await fetch('https://www.amiiboapi.com/api/amiibo/')
  const data = await response.json()
  amiibos.value = data.amiibo
})

const paginated = computed(() => {
  return amiibos.value.slice(0, page.value * perPage)
  
})

function nextPage() {
  page.value++
}
</script>
