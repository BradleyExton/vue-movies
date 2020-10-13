<template>
  <div class="bg-gray-200 w-full">
    <div class="max-w-6xl px-10 pb-10 m-auto">
      <h3 class="text-xl text-gray-500 mb-16 font-mono flex justify-center">
        - Movie List -
      </h3>
      <div class="flex flex-col items-center sm:flex-row flex-wrap">
        <div
          class="rounded shadow-2xl bg-white w-56 flex flex-col justify-center items-center pb-5 pt-3 px-3 sm:mr-5 mb-5 cursor-pointer transform duration-300 ease-in-out hover:scale-105"
          v-for="movie in movies"
          :key="movie.imdbID"
          @click="$emit('set-active-movie', movie)"
        >
          <p
            class="font-bold text-center align-middle mb-3 h-16 flex items-center"
          >
            {{ movie.Title }}
          </p>
          <MoviePoster class="h-56" :poster="movie.Poster" :small="true" />
        </div>
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
