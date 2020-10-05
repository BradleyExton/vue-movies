<template>
  <div class="w-full bg-gray-200 px-20 pb-10">
    <h3 class="text-xl text-gray-700 mb-5">- Movie List -</h3>
    <div class="flex flex-wrap">
      <div
        class="rounded shadow-2xl bg-white w-56 flex flex-col items-center pb-5 pt-3 mr-5 mb-5 cursor-pointer"
        v-for="movie in movies"
        :key="movie.Title"
      >
        <p class="font-bold text-center align-middle mb-3">{{ movie.Title }}</p>
        <img class="w-40" :src="movie.Poster" />
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "movie-list",
  props: {
    movies: Array,
  },
};
</script>

<style></style>
