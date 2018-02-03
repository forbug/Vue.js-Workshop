<template>
  <div class="row">
    <div class="col-lg-12 text-center">

      <img src="@/assets/logo.png">

      <h1>{{ msg }}</h1>

      <p class="subtitle">
        Built with Vue.js, Bootstrap, and FontAwesome
        <i class="fa fa-thumbs-up"></i>
      </p>

    </div>
  </div>
</template>

<!-- // // // // -->

<script>

export default {
  name: 'Hello',
  data () {
    return {
      msg: 'Welcome to the RCOS Vue.js Workshop'
    }
  }
}

</script>

<!-- // // // // -->

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  p.subtitle {
    font-size: 2rem;
    color: #999999;
  }
</style>
