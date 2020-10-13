<template>
  <div
    class="pb-16 bg-gray-200 flex justify-center max-w-6xl items-center px-10 min-h-180"
    v-bind:class="{
      'flex justify-center items-center': !activeMovie.Title,
    }"
  >
    <transition name="fade">
      <div
        v-show="displayMovieDetails && !!activeMovie.Title"
        class="min-w-full flex text-gray-700 rounded shadow-2xl p-5 mt-16 bg-white flex-grow z-10"
      >
        <div
          class="flex flex-col justify-center lg:flex-row"
          key="movie-details"
        >
          <Poster class="m-auto pt-5 lg:p-10" :poster="activeMovie.Poster" />
          <div class="max-w-2xl m-5 md:m-10">
            <p
              class="font-bold text-xl mb-3 text-gray-900 font-mono text-center lg:mt-5"
            >
              {{ activeMovie.Title }}
            </p>
            <p class="flex items-center mb-5">
              <icon-base
                class="mt-1"
                width="35"
                height="35"
                icon-name="director"
              >
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
            <div class="ml-10">
              <button
                v-if="movieExistsInList(activeMovie)"
                @click="$emit('remove-movie', activeMovie)"
                class="bg-red-600 hover:bg-red-700 text-white font-bold py-2 px-4 rounded mt-8 md:mt-12 lg:mt-20"
              >
                Remove From List
              </button>
              <button
                v-else
                @click="$emit('add-movie')"
                class="bg-blue-500 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded mt-8 md:mt-12 lg:mt-20"
              >
                Add To List
              </button>
            </div>
          </div>
        </div>
      </div>
    </transition>
    <transition name="fade">
      <div
        class="absolute text-center flex text-gray-700 rounded shadow-2xl p-5 mt-16 bg-white px-32 mb-12 z-10"
        v-show="displayMovieDetails && !activeMovie.Title"
        key="no-movie"
      >
        No Movie was found...
      </div>
    </transition>
    <div
      class="flex justify-center items-center h-full text-gray-500 font-mono text-center absolute"
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
import Poster from "./MoviePoster";

export default {
  name: "movie-details",
  props: {
    activeMovie: Object,
    displayMovieDetails: Boolean,
    movieExistsInList: Function,
  },
  components: { ActorsIcon, DateIcon, DirectorIcon, IconBase, Poster },
};
</script>

<style>
.fade-enter-active,
.fade-leave-active {
  transition: all .25s;
  opacity: 1;
  transform: translate(0px, 0px);
}
.fade-enter, .fade-leave-to, .fade-leave /* .fade-leave-active below version 2.1.8 */ {
  opacity: 0;
  transform: translate(0px, -100px);
}
</style>
