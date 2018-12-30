<template>
  <div class="form">
    <h1>Login</h1>
    <form @submit.prevent="onSubmit">
      <div class="form-group">
        <label>Email address</label>
        <input 
          type="email" 
          class="form-control" 
          aria-describedby="emailHelp" 
          :placeholder="placeholder.email"
          v-model="user.email"
          required
        >
      </div>

      <div class="form-group">
        <label>Password</label>
        <input 
          type="password" 
          class="form-control" 
          :placeholder="placeholder.password"
          v-model="user.password"
          required
        >
      </div>
      <button type="submit" class="btn btn-dark">Login</button>
    </form>
    <small><router-link :to="{ name: 'register' }">Don't have an account yet? Register here...</router-link></small>

    <form-error v-if="errors">{{ errors }}</form-error>
  </div>
</template>

<script>
import { mapActions, mapGetters } from 'vuex'
import FormError from './../partials/FormError'

export default {
  components: {
    FormError
  },
  data() {
    return {
      user: {},
      placeholder: {
        email: `\uf0e0 Enter Email`,
        password: `\uf023 Password`
      }
    }
  },
  methods: {
    ...mapActions(['login']),
    onSubmit() {
      this.login(this.user)
    }
  },
  computed: {
    ...mapGetters({
      errors: 'getErrors'
    })
  }
}
</script>

<style scoped>
h1 {
  margin: 1rem 0;
}

.form {
  max-width: 500px;
}
</style>
