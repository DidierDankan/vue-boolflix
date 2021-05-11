<template>
  <div id="app">
    <!-- header -->
    <Header @performSearch="searchInfo" />
    <!-- main content -->

    <Main :listOfSearch="filteredMovies" />
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
        "https://api.themoviedb.org/3/search/movie?api_key=601edd5f9c75134b378e20f00be3a1bb&query=Mortal-Kombat",
      movies: [],
      filteredMovies: [],
      // flags: ["@/assets/img/en.png", "@/assets/img/it.png"],
      loading: true,
      searching: "",
    };
  },
  computed: {
    searchMovieSerie() {
      if (
        this.movies[0].title
          .toLowerCase()
          .includes(this.searching.toLowerCase())
      ) {
        this.filteredMovies = this.movies;
      }
      return this.filteredMovies;
    },
  },
  created() {
    this.getMovies();
    console.log(this.filteredMovies);
  },
  methods: {
    getMovies() {
      /**
       * API call
       */
      axios
        .get(this.apiURL)
        .then((res) => {
          this.movies = res.data.results;
          console.log(this.movies);
        })
        .catch((err) => {
          console.log("error", err);
        });
    },

    // searchMovieSerie(searching) {
    //   if (
    //     this.movies[0].title.toLowerCase().includes(searching.toLowerCase())
    //   ) {
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
