<template>

    <div id="app">
      <nav-bar></nav-bar>
      <transition>
        <router-view class="container"></router-view>
      </transition>
      

  </div>
</template>

<script>
import NavBar from './components/partials/NavBar'



export default {
  name: 'app',
  components: {
    NavBar,


  }
}
</script>

<style>
#app {
  font-family: 'Roboto', sans-serif;  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

h1 {
  margin-top: 1rem !important;
}

input, textarea {
  font-family: FontAwesome, "Open Sans", Verdana, sans-serif !important;
}
</style>
