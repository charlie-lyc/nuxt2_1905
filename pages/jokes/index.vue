<template>
  <div>
    <!-- Jokes -->

    <SearchJokes @search-word="handleSearchWord"/>
    
    <Joke v-for="joke in jokes" :key="joke.id" :joke="joke"/>

  </div>
</template>

<script>
// import axios from '@nuxtjs/axios'  // <= 임포트할 수 없음 !!!
import axios from 'axios' // <= @nuxtjs/axios": "^5.3.6" 으로 설치 되어야 함
import Joke from '../../components/Joke.vue'
import SearchJokes from '../../components/SearchJokes.vue'

export default {
  components: {
    Joke,
    SearchJokes,
  },
  head() {
    return {
      title: 'Dad Jokes',
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
      jokes: []
    }
  },
  async created() {
    //////////////////////////////////////////
    const config = {
      headers: { 'Accept': 'application/json'}
    }
    //////////////////////////////////////////
    try {
      const res = await axios.get(`https://icanhazdadjoke.com/search`, config)
      // console.log(res.data.results)
      this.jokes = res.data.results
    } catch (err) {
      console.log(err)
    }
  },
  methods: {
    async handleSearchWord(word) {
      //////////////////////////////////////////
      const config = {
        headers: { 'Accept': 'application/json'}
      }
      //////////////////////////////////////////
      try {
        const res = await axios.get(`https://icanhazdadjoke.com/search?term=${word}`, config)
        // console.log(res.data.results)
        this.jokes = res.data.results
      } catch (err) {
        console.log(err)
      }
    }
  }

}
</script>