<template>
  <div id="app">
    <!-- header -->
    <Header @performSearch="getSearch" />
    <!-- main content -->

    <Main
      :listOfMovies="movies"
      :searchResult="searching"
      :listOfSeries="series"
    />
  </div>
</template>

<script>
import axios from "axios";
// :searchResult="searching"
import Header from "./components/Header";
import Main from "./components/Main";

export default {
  name: "App",
  components: {
    Header,
    Main,
  },
  data() {
    return {
      apiURLMovie: "https://api.themoviedb.org/3/search/",
      apiURLTv: "https://api.themoviedb.org/3/search/",
      movies: [],
      series: [],
      // filteredMovies: [],
      // flags: ["@/assets/img/en.png", "@/assets/img/it.png"],
      loading: true,
      searching: "",
    };
  },
  methods: {
    getSearch(searchText) {
      /**
       * API call of movies
       */
      if (searchText !== "") {
        axios
          .get(this.apiURLMovie + "movie", {
            params: {
              api_key: "601edd5f9c75134b378e20f00be3a1bb",
              query: searchText,
            },
          })
          .then((res) => {
            this.movies = res.data.results;
          });

        /**
         * API call series
         */
        axios
          .get(this.apiURLTv + "tv", {
            params: {
              api_key: "601edd5f9c75134b378e20f00be3a1bb",
              query: searchText,
            },
          })
          .then((res) => {
            this.series = res.data.results;
          });
      }
    },
  },
};
</script>

<style lang="scss">
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
body {
  font-family: sans-serif;
}
</style>
