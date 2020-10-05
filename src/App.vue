<template>
  <div id="app" class="h-screen flex flex-col bg-gray-200">
    <header
      class="w-full bg-white px-20 h-20 flex flex-none justify-between items-center shadow z-10"
    >
      <div class="text-3xl font-mono font-bold flex">
        <h3 class="text-pink-600 text-3xl font-mono font-bold">VUE</h3>
        <h3 class="text-pink-900 mr-1 text-3xl font-mono font-bold">Movies</h3>

        <icon-base width="38" height="38" icon-name="movie" iconColor="#702459">
          <movie-icon />
        </icon-base>
      </div>
      <form class="flex justify-end h-10" @submit.prevent="searchForMovie">
        <input
          class="shadow appearance-none border rounded w-64 py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:shadow-outline"
          id="Search"
          v-model="searchTitle"
          type="text"
          placeholder="Movie Title..."
        /><button
          class="bg-blue-500 hover:bg-blue-700 text-white font-bold py-2 px-4 ml-5 rounded"
        >
          Search
        </button>
      </form>
    </header>
    <MovieDetails
      :activeMovie="activeMovie"
      :displayMovieDetails="displayMovieDetails"
      :movieExistsInList="movieExistsInList"
      @add-movie="addActiveMovieToList"
      @remove-movie="removeMovieFromList"
    />
    <MovieList :movies="movies" @set-active-movie="setActiveMovie" />
  </div>
</template>

<script>
import MovieList from "./components/MovieList";
import MovieDetails from "./components/MovieDetails";
import IconBase from "./components/icons/IconBase";
import MovieIcon from "./components/icons/MovieIcon";

export default {
  name: "App",
  components: { MovieList, MovieDetails, IconBase, MovieIcon },
  data() {
    return {
      activeMovie: {},
      movies: [],
      searchTitle: "",
      displayMovieDetails: false,
    };
  },
  methods: {
    async searchForMovie() {
      try {
        const response = await fetch(
          `http://www.omdbapi.com/?i=tt3896198&apikey=f7842b9a&t='${this.searchTitle}'`
        );
        const data = await response.json();
        this.setActiveMovie(data);
        this.displayMovieDetails = true;
      } catch (error) {
        this.displayMovieDetails = false;
        console.error(error);
      }
    },
    addActiveMovieToList() {
      this.movies = [...this.movies, this.activeMovie];
    },
    removeMovieFromList(movie) {
      this.movies = this.movies.filter((mov) => mov.imdbID !== movie.imdbID);
    },
    setActiveMovie(movie) {
      this.activeMovie = movie;
    },
    movieExistsInList(movie) {
      const movieInList = this.movies.find(
        (mov) => mov.imdbID === movie.imdbID
      );
      return !!movieInList;
    },
  },
};
</script>

<style></style>
