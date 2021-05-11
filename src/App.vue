<template>
  <div id="app">
    <!-- header -->
    <Header @performSearch="searchInfo" />
    <!-- main content -->

    <Main :listOfSearch="getMovies" />
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
      apiURL:
        "https://api.themoviedb.org/3/search/movie?api_key=601edd5f9c75134b378e20f00be3a1bb",
      movies: [],
      // filteredMovies: [],
      // flags: ["@/assets/img/en.png", "@/assets/img/it.png"],
      loading: true,
      searching: "",
    };
  },
  computed: {},
  created() {},
  methods: {
    // getMovies() {
    //   /**
    //    * API call
    //    */
    //   axios
    //     .get(this.apiURL, {
    //       params: {
    //         query: this.searching,
    //       },
    //     })
    //     .then((res) => {
    //       this.movies = res.data.results;
    //       console.log(this.movies);
    //     })
    //     .catch((err) => {
    //       console.log("error", err);
    //     });
    // },
    getMovies() {
      /**
       * API call
       */
      axios
        .get(this.apiURL, {
          params: {
            query: this.searching,
          },
        })
        .then((res) => {
          this.movies = res.data.results;
          console.log(this.movies);
        })
        .catch((err) => {
          console.log("error", err);
        });
    },

    // searchMovieSerie() {
    //   if (this.movies[0].title.toLowerCase() === this.searching.toLowerCase()) {
    //     this.filteredMovies = this.movies;
    //   }
    //   return this.filteredMovies;
    // },

    searchInfo(searchText) {
      this.searching = searchText.toLowerCase();
    },
  },
};
</script>

<style lang="scss"></style>
