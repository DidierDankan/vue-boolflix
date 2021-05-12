<template>
  <div id="app">
    <!-- header -->
    <Header @performSearch="searchInfo" />
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
      apiURLMovie: "https://api.themoviedb.org/3/search/movie",
      apiURLTv: "https://api.themoviedb.org/3/search/tv",
      movies: [],
      series: [],
      // filteredMovies: [],
      // flags: ["@/assets/img/en.png", "@/assets/img/it.png"],
      loading: true,
      searching: "",
    };
  },
  methods: {
    getMovies() {
      /**
       * API call of movies
       */
      if (this.searching !== "") {
        axios
          .get(this.apiURLMovie, {
            params: {
              api_key: "601edd5f9c75134b378e20f00be3a1bb",
              query: this.searching,
            },
          })
          .then((res) => {
            this.movies = res.data.results;
          })
          .catch((err) => {
            console.log("error", err);
          });
      }
    },

    getSeries() {
      /**
       * API call series
       */
      if (this.searching !== "") {
        axios
          .get(this.apiURLTv, {
            params: {
              api_key: "601edd5f9c75134b378e20f00be3a1bb",
              query: this.searching,
            },
          })
          .then((res) => {
            this.series = res.data.results;
          })
          .catch((err) => {
            console.log("error", err);
          });
      }
    },

    searchInfo(searchText) {
      this.searching = searchText.toLowerCase();
      this.getMovies();
      this.getSeries();
    },
  },
};
</script>

<style lang="scss"></style>
