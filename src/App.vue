<template>
  <div id="app">
    <!-- header -->
    <Header @performSearch="searchInfo" />
    <!-- main content -->

    <Main
      :listOfSearch="movies"
      :searchResult="searching"
      :flagLanguage="flags"
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
      apiURL:
        "https://api.themoviedb.org/3/search/movie?api_key=601edd5f9c75134b378e20f00be3a1bb&query=Mortal-Kombat",
      movies: [],
      flags: ["@/assets/img/en.png", "@/assets/img/it.png"],
      loading: true,
      searching: "",
    };
  },
  created() {
    this.getMovies();
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
        })
        .catch((err) => {
          console.log("error", err);
        });
    },
    searchInfo(searchText) {
      this.searching = searchText.toLowerCase();
    },
  },
};
</script>

<style lang="scss"></style>
