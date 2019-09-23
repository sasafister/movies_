<template>
  <div class="flex">
    <swiper :options="swiperOption">
    <swiper-slide v-for="movie in movies" :key="movie.imdbID">
      <router-link :to="`/movie/${movie.imdbID}`" class="z-50">
        <img :src="movie.Poster" class="w-48 rounded-lg mx-auto z-10" alt="">
        <div class="text-grey-400 text-lg my-10 font-semibold z-10">{{ movie.Title }}</div>
      </router-link>
    </swiper-slide>
    <div class="swiper-pagination" slot="pagination"></div>
  </swiper>
  </div>
</template>

<script>
export default {
  name: 'Movies',
  props: ['movies'],
  data() {
    return {
      swiperOption: {
        slidesPerView: 3,
        spaceBetween: 30,
        pagination: {
          el: '.swiper-pagination',
          clickable: true
        }
      }
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>
