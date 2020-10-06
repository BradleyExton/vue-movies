<template>
  <div class="w-full bg-gray-200 px-20 pb-10">
    <h3 class="text-xl text-gray-500 mb-5 font-mono flex justify-center">
      - Movie List -
    </h3>
    <div class="flex flex-wrap">
      <div
        class="rounded shadow-2xl bg-white w-56 flex flex-col justify-center items-center pb-5 pt-3 px-3 mr-5 mb-5 cursor-pointer"
        v-for="movie in movies"
        :key="movie.imdbID"
        @click="$emit('set-active-movie', movie)"
      >
        <p class="font-bold text-center align-middle mb-3">{{ movie.Title }}</p>
        <MoviePoster :poster="movie.Poster" :small="true" />
      </div>
    </div>
  </div>
</template>

<script>
import MoviePoster from "../components/MoviePoster";
export default {
  name: "movie-list",
  props: {
    movies: Array,
  },
  components: {
    MoviePoster,
  },
};
</script>

<style></style>
