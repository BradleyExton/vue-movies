<template>
  <div class="flex-grow mx-16 my-5">
    <form class="flex justify-end" @submit.prevent="handleSearch">
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
  </div></template
>

<script>
export default {
  name: "movie-details",
  methods: {
    handleSearch() {
      this.$emit("search:movie", this.searchTitle);
    },
  },

  data() {
    return {
      searchTitle: "",
    };
  },
};
</script>

<style></style>
