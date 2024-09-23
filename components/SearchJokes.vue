<template>

  <!-- <form 
    @submit="onSubmit"
  > -->
  <form 
    @submit.prevent="onSubmit"
  >
    <input type="text" placeholder="Search Jokes ..."
      v-model="searchWord"
    />
    <input type="submit" value="Search Jokes" />
  </form>

</template>

<script>
export default {
  name: 'SearchJokes',
  data() {
    return {
      searchWord: '',
    }
  },
  methods: {
    onSubmit(e) {
      // e.preventDefault()
      this.$emit('search-word', this.searchWord)
      this.searchWord = ''
    }
  }
}
</script>

<style>

</style>