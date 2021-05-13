<template>
  <div id="app">
    <!-- header -->
    <Header @performSearch="getSearch" />
    <!-- main content -->

    <Main
      :listOfMovies="movies"
      :searchResult="searching"
      :listOfSeries="series"
      :listOfPopular="popularMovies"
      :listOfPopSeries="popularSeries"
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
      apiURL: "https://api.themoviedb.org/3/search/",
      apiURLPop: "https://api.themoviedb.org/3/discover/",
      apiURLSerie: "https://api.themoviedb.org/3/tv/",
      movies: [],
      series: [],
      popularMovies: [],
      popularSeries: [],
      // filteredMovies: [],
      // flags: ["@/assets/img/en.png", "@/assets/img/it.png"],
      loading: true,
      searching: "",
    };
  },
  created() {
    this.getPopularMovies();
    this.getPopularSeries();
  },
  methods: {
    getPopularSeries() {
      /**
       * API call for popular series home page
       */
      axios
        .get(this.apiURLSerie + "popular", {
          params: {
            api_key: "601edd5f9c75134b378e20f00be3a1bb",
            sort_by: "popularity.desc",
          },
        })
        .then((res) => {
          this.popularSeries = res.data.results;
        });
    },
    getPopularMovies() {
      /**
       * API call for popular movies home page
       */
      axios
        .get(this.apiURLPop + "movie", {
          params: {
            api_key: "601edd5f9c75134b378e20f00be3a1bb",
            sort_by: "popularity.desc",
          },
        })
        .then((res) => {
          this.popularMovies = res.data.results;
        });
    },
    getSearch(searchText) {
      /**
       * API call of movies
       */
      if (searchText !== "") {
        axios
          .get(this.apiURL + "movie", {
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
          .get(this.apiURL + "tv", {
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
  scrollbar-width: thin;
  scrollbar-color: #fff #1a1818;
}
body {
  font-family: sans-serif;
}
</style>
