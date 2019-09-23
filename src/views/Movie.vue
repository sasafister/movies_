<template>
  <div v-if="movie" class="max-w-sm rounded overflow-hidden shadow-lg mx-auto mt-12">
    <div @click="$router.go(-1)" class="text-grey-300 pb-4 underline cursor-pointer">Back</div>
    <img class="w-full" :src="movie.Poster" alt="Sunset in the mountains">
    <div class="px-6 py-4">
      <div class="font-bold text-xl mb-2">{{ movie.Title }}</div>
      <p class="text-gray-700 text-base">
        {{ movie.Plot }}
      </p>
    </div>
    <div class="px-6 py-4">
      <span class="inline-block bg-gray-200 rounded-full px-3 py-1 text-sm font-semibold text-gray-700 mr-2">Released: {{ movie.Released }}</span>
      <span class="inline-block bg-gray-200 rounded-full px-3 py-1 text-sm font-semibold text-gray-700 mr-2">{{ movie.Production }}</span>
    </div>
  </div>
</template>

<script>
  import axios from 'axios'

  export default {
    name: 'movie',
    data() {
      return {
        movieId: this.$route.params.movieId,
        movie: {}
      }
    },
    mounted() {
      axios.get(`http://www.omdbapi.com/?i=${this.movieId}&apikey=c5d4c16`).then(response => {
        console.log(response.data)
        this.movie = response.data
      })
    }
  }
</script>
