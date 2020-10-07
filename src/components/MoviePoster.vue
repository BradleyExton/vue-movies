<template>
  <img
    v-if="poster !== 'N/A'"
    class="rounded"
    v-bind:class="{ 'w-40': small }"
    :src="poster"
  />
  <div
    v-else
    class="bg-purple-300 opacity-75 rounded text-gray-600 font-mono flex justify-center items-center"
    v-bind:class="{ 'w-40 h-56': small, ' w-48 h-56': !small }"
  >
    No Poster
  </div>
</template>

<script>
export default {
  name: "movie-poster",
  props: {
    poster: String,
    small: Boolean,
  },
};
</script>