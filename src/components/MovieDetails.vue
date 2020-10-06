<template>
  <div class="pt-5 pb-16 bg-gray-200 min-h-156">
    <div
      v-if="displayMovieDetails"
      class="py-8 flex text-gray-700 rounded shadow-2xl p-10 mt-5 bg-white mx-20"
    >
      <img class="shadow" :src="activeMovie.Poster" />
      <div class="ml-10">
        <p class="font-bold text-xl ml-12 mb-3 text-gray-900 font-mono">
          {{ activeMovie.Title }}
        </p>
        <p class="flex items-center mb-5">
          <icon-base class="mt-1" width="35" height="35" icon-name="director">
            <director-icon />
          </icon-base>
          <span class="ml-3">{{ activeMovie.Director }}</span>
        </p>
        <p class="flex items-center mb-6">
          <icon-base class="mt-1" width="35" height="35" icon-name="actors">
            <actors-icon />
          </icon-base>
          <span class="ml-3">{{ activeMovie.Actors }}</span>
        </p>
        <p class="flex items-center mb-5">
          <icon-base width="35" height="35" icon-name="release">
            <date-icon />
          </icon-base>
          <span class="ml-3">{{ activeMovie.Year }}</span>
        </p>
        <p class="mt-10 ml-10 pl-1">{{ activeMovie.Plot }}</p>
        <button
          v-if="movieExistsInList(activeMovie)"
          @click="$emit('remove-movie', activeMovie)"
          class="bg-red-600 hover:bg-red-700 text-white font-bold py-2 px-4 ml-10 rounded mt-10"
        >
          Remove From List
        </button>
        <button
          v-else
          @click="$emit('add-movie')"
          class="bg-blue-500 hover:bg-blue-700 text-white font-bold py-2 px-4 ml-10 rounded mt-10"
        >
          Add To List
        </button>
      </div>
    </div>
    <div
      class="flex justify-center items-center h-full text-gray-500 font-mono"
      v-else
    >
      Please search for a movie above....
    </div>
  </div>
</template>

<script>
import ActorsIcon from "./icons/ActorsIcon";
import DateIcon from "./icons/DateIcon";
import DirectorIcon from "./icons/DirectorIcon";
import IconBase from "./icons/IconBase";

export default {
  name: "movie-details",
  props: {
    activeMovie: Object,
    displayMovieDetails: Boolean,
    movieExistsInList: Function,
  },
  components: { ActorsIcon, DateIcon, DirectorIcon, IconBase },
};
</script>

<style></style>
