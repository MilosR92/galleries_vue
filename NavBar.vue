<template>
  <nav class="navbar navbar-expand-lg navbar-dark bg-dark">
    <div class="container">

      <router-link 
        :to="{ name: 'home' }"
        class="navbar-brand">
        <strong>Galleries</strong>
      </router-link>

      <button class="navbar-toggler" type="button" data-toggle="collapse" data-target="#navbarSupportedContent" aria-controls="navbarSupportedContent" aria-expanded="false" aria-label="Toggle navigation">
        <span class="navbar-toggler-icon"></span>
      </button>

      <div class="collapse navbar-collapse" id="navbarSupportedContent">
        <ul class="navbar-nav mr-auto">
          <li class="nav-item">
          <router-link 
            :to="{ name: 'home' }"
            class="nav-link"
          >
            All Galleries
          </router-link>                
        </li>  
        <li 
          v-if="user"
          class="nav-item"
        >
          <router-link 
            :to="{ name: 'my-galleries' }"
            class="nav-link"
          >
            My Galleries
          </router-link>                
        </li> 
        <li 
          v-if="user"
          class="nav-item"
        >
          <router-link 
            :to="{ name: 'create-gallery' }"
            class="nav-link"
          >
            Create New Gallery
          </router-link>                
        </li>
        </ul>
        <ul 
        v-if="!user"
        class="navbar-nav"
      >
        <li class="nav-item">
          <router-link 
            :to="{ name: 'login'}"
            class="nav-link"
          >
            Login
          </router-link>
        </li>
        <li class="nav-item">
          <router-link 
            :to="{ name: 'register'}"
            class="nav-link"
          >
            Register
          </router-link>
        </li>
      </ul>
      <ul 
        v-else
        class="navbar-nav"
      >
        <li class="nav-item">
          <button             
            class="btn btn-dark"
            @click="onClick"
          >
            Logout
          </button>
        </li>
      </ul>
      </div>
    </div>
  </nav>
</template>

<script>
import { mapGetters, mapActions } from 'vuex'
import Vue from 'vue'
import VueRouter from 'vue-router'

Vue.use(VueRouter)



export default {
  computed: {
    ...mapGetters({
      user: 'getUser'
    })
  },
  methods: {
    ...mapActions(['logout']),
    onClick() {
      this.logout()
    }
  },    
}
</script>

<style scoped>
.btn {
  margin: 0 !important;
}
</style>
