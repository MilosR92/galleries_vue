<template>
  <form 
    class="form-inline"
    
    @submit.prevent="onSearch"           
  >
    <input 
      class="form-control" 
      type="search" 
      :placeholder="placeholder" 
      aria-label="Search"
      v-model="term"
      autofocus
    >
    <button 
      class="btn btn-outline-dark" 
      type="submit"
    >
      Filter Galleries
    </button>
  </form>
</template>

<script>
export default {
  data() {
    return {
      term: '',
      placeholder: `\uf002 Filter`
    }
  },
  methods: {
    onSearch() {
      this.$emit('search', this.term)
    }
  }
}
</script>

<style>
.form-inline {
  margin: 1rem;
  display: block !important;
}

.btn {
  margin: 1rem;
}
</style>
