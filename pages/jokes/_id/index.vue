<template>
  <div>
    <!-- (this.)$route, (this.)$emit, ... -->

    <nuxt-link to="/jokes">Back to Jokes</nuxt-link>
    <hr />

    <!-- 
    <h2>{{ joke.joke }}</h2>
    <hr />
    <small>Joke ID : {{ joke.id }}</small> 
    -->
    <!-- ////////////////////////////////////////// -->
    <h2>{{ joke }}</h2>
    <hr />
    <small>Joke ID : {{ $route.params.id }}</small>

  
  </div>
</template>

<script>
import axios from 'axios'

export default {
  head() {
    return {
      title: this.joke, // <= !!!
      meta: [
        {
          hid: 'description',
          name: 'description',
          content: 'Best place for corny dad jokes'
        }
      ]
    }
  },
  data() {
    return {
        // joke: {},
        /////////////
        joke: '',
    }
  },
  async created() {
    //////////////////////////////////////////
    const config = {
      headers: { 'Accept': 'application/json'}
    }
    //////////////////////////////////////////
    try {
      const res = await axios.get(`https://icanhazdadjoke.com/j/${this.$route.params.id}`, config)
      // console.log(res.data)
      // this.joke = res.data
      ///////////////////////////
      console.log(res.data.joke)
      this.joke = res.data.joke
    } catch (err) {
      console.log(err)
    }
  },
}
</script>

<style>

</style>