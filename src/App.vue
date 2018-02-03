<template>
  <div>

    <nav class="navbar bg-dark text-light">
      <a class="navbar-brand">Vue.js Workshop</a>
      <ul class="navbar-nav ml-auto">
        <li class="nav-item">
          <a class="nav-link" target="_blank" href="https://rcos.io">RCOS</a>
        </li>
      </ul>
    </nav>

    <div id="app" class="container">
      <router-view/>
    </div>

  </div>

</template>

<script>
export default {
  name: 'App'
}
</script>
