<template>
  <div id="app" class="h-screen">
    <header
      class="w-full bg-teal-100 pl-16 py-3 text-3xl flex font-mono shadow z-10"
    >
      <h3 class="text-pink-600">VUE</h3>
      <h3 class="text-pink-900 ">Movies</h3>
    </header>
    <div class="flex h-full">
      <MovieDetails @search:movie="searchForMovie" />
      <MovieList />
    </div>
  </div>
</template>

<script>
import MovieList from "./components/MovieList";
import MovieDetails from "./components/MovieDetails";

export default {
  name: "App",
  components: { MovieList, MovieDetails },
  data() {
    return {
      activeMovie: {},
    };
  },
  methods: {
    async searchForMovie(title) {
      try {
        const response = await fetch(
          `http://www.omdbapi.com/?i=tt3896198&apikey=f7842b9a&t='${title}'`
        );
        const data = await response.json();
        console.log("Data: ", data);
        this.activeMovie = data;
      } catch (error) {
        console.error(error);
      }
    },
  },
};
</script>

<style></style>
