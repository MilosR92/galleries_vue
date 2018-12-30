<template>
  <div class="comment-form">
    <h5>Add a Comment</h5>
    <div class="form-group">
      <textarea 
        class="form-control"
        v-model="body"
        @keydown.enter.prevent="onSubmit"
        :placeholder="placeholder"
        maxlength="1000"
        required        
      ></textarea>
    </div>
    <div v-if="errors.body">
      <form-error>{{ errors.body[0]}}</form-error>
    </div>
  </div>
</template>

<script>
import FormError from './FormError'

export default {
  components: {
    FormError
  },
  props: ['errors'],
  data() {
    return {
      body: '',
      placeholder: `\uf075 Comment here`
    }
  },
  methods: {
    onSubmit() {
      if(this.body) {
        this.$emit('submitComment', this.body)
        this.body = ''
      }
    }
  }
}
</script>

<style scoped>
.comment-form {
  margin-top: 1rem;
}
</style>
