
<template>
  <!-- Footer -->
  <footer id="footer">
    <div class="container">
      <div class="row">
        <div class="col-12">
          <ul class="actions">
            <li>
              <RouterLink to="/list" class="button large">Liste complète</RouterLink>
            </li>
          </ul>
        </div>
      </div>
      <div class="row mt-4">
        <div class="col-12">
          <div id="copyright">
            <ul class="links">
              <li>&copy; AmiiVue ~ 2024</li>
              <li>Design: <a href="http://html5up.net">HTML5 UP</a></li>
            </ul>
          </div>
        </div>
      </div>
    </div>
  </footer>
</template>

<script setup>
import { RouterLink } from 'vue-router'
</script>
