<template>
  <div>
    <input type="text" class="py-2 px-3 w-1/3 border rounded-lg mt-16" @input="searchChanged" placeholder="Search movies">
    <movies :movies="movies" class="mx-12 mt-10"/>
  </div>
</template>

<script>
// @ is an alias to /src
import Movies from '@/components/Movies.vue'
import axios from 'axios'

export default {
  name: 'home',
  components: {
    Movies
  },
  data() {
    return {
      term: '',
      movies: []
    }
  },
  methods: {
    searchChanged(e) {
      this.term = e.target.value
      this.getMovies()
    },
    getMovies() {
      axios.get(`http://www.omdbapi.com/?s=${this.term}&apikey=c5d4c16`).then(response => {
        this.movies = response.data.Search
      })
    }
  }
}
</script>
