<template>
  <div class="form">
    <h1>Register</h1>
    <form @submit.prevent="onSubmit">
      <div class="form-group">
        <label>First Name</label>
        <input 
          type="text" 
          class="form-control" 
          aria-describedby="emailHelp" 
          :placeholder="placeholder.first_name"
          v-model="user.first_name"
          required
        >
        <div v-if="errors">
          <form-error v-if="errors.first_name">{{ errors.first_name[0] }}</form-error>
        </div>
      </div>

      <div class="form-group">
        <label>Last Name</label>
        <input 
          type="text" 
          class="form-control" 
          aria-describedby="emailHelp" 
          :placeholder="placeholder.last_name"
          v-model="user.last_name"
          required
        >
        <div v-if="errors">
          <form-error v-if="errors.last_name">{{ errors.last_name[0] }}</form-error>
        </div>
      </div>

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
        <div v-if="errors">
          <form-error v-if="errors.email">{{ errors.email[0] }}</form-error>
        </div>
      </div>

      <div class="form-group">
        <label>Password</label>
        <input 
          type="password" 
          class="form-control" 
          :placeholder="placeholder.password"
          v-model="user.password"
          pattern="(?=.*\d).{8,}"
          required
        >
        <div v-if="errors">
          <form-error v-if="errors.password">{{ errors.password[0] }}</form-error>
        </div>
      </div>

      <div class="form-group">
        <label>Confirm Password</label>
        <input 
          type="password" 
          class="form-control" 
          :placeholder="placeholder.password_confirmation"
          v-model="user.password_confirmation"
          required
        >
        <div v-if="errors">
          <form-error v-if="errors.password_confirmation">{{ errors.password_confirmation[0] }}</form-error>
        </div>
      </div>

      <div class="form-group form-check">
        <input 
          type="checkbox" 
          class="form-check-input"
          v-model="user.terms"
          id="terms"
          required
        >
        <label 
          for="terms" 
          class="form-check-label"
        >
          Check to accept Terms and Conditions
        </label>
        <div v-if="errors">
          <form-error v-if="errors.terms">{{ errors.terms[0] }}</form-error>
        </div>
      </div>

      <button type="submit" class="btn btn-dark">Register</button>
    </form>
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
        first_name: `\uf007 First Name`,
        last_name: `\uf007 Last Name`,
        email: `\uf0e0 Enter Email`,
        password: `\uf023 Choose Password (minimum 8 characters, 1 number)`,
        password_confirmation: `\uf023 Confirm Password`
      }
    }
  },
  methods: {
    ...mapActions(['register']),
    onSubmit() {
      this.register(this.user)
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