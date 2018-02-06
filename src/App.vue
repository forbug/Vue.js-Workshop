<template>
  <div>

    <nav class="navbar bg-dark text-light">
      <a class="navbar-brand" href="#/">Vue.js Workshop</a>

      <ul class="navbar-nav mr-auto">
        <li class="nav-item">
          <a class="nav-link" href="#/todos">ToDo List</a>
        </li>
      </ul>

      <ul class="navbar-nav ml-auto">
        <li class="nav-item">
          <a class="nav-link" target="_blank" href="https://rcos.io">RCOS</a>
        </li>
      </ul>
    </nav>

    <div id="app" class="container pt-4">
      <router-view/>
    </div>

    <footer>
      <div class="container">
        <div class="row">
          <div class="col-lg-12">
            <p class="lead">

              Built with
              <a href="https://fontawesome.bootstrapcheatsheets.com/" target="_blank">
                Vue.js
              </a>,
              <a href="https://fontawesome.bootstrapcheatsheets.com/" target="_blank">
                Bootstrap
              </a>,
              &amp;
              <a href="https://fontawesome.bootstrapcheatsheets.com/" target="_blank">
                FontAwesome
              </a>
              <i class="fa fa-thumbs-up"></i>
            </p>
          </div>
        </div>
      </div>
    </footer>

  </div>

</template>

<script>
export default {
  name: 'App'
}
</script>

<style type="text/css">
  footer {
    position: absolute;
    bottom: 0;
  }
</style>
