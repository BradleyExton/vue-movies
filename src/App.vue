<template>
  <div id="app">
    <header>Vue Movies</header>
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
