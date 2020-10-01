<template>
  <div id="app">
    <header
      class="w-full bg-teal-100 pl-16 py-3 text-3xl flex font-mono shadow"
    >
      <h3 class="text-pink-600">VUE</h3>
      <h3 class="text-pink-900 ">Movies</h3>
    </header>
    <div>
      <MovieList />
      <MovieDetails />
    </div>
  </div>
</template>

<script>
import MovieList from "./components/MovieList";
import MovieDetails from "./components/MovieDetails";

export default {
  name: "App",
  components: { MovieList, MovieDetails },
};
</script>

<style></style>
