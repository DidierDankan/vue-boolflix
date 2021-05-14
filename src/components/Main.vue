<template>
  <main>
    <!-- popular movies -->
    <section v-show="listOfMovies.length === 0 && listOfSeries.length === 0">
      <h2>Popular Movies</h2>
      <div class="card-expo">
        <CardHome
          @click="movieInfo(movie)"
          v-for="movie in listOfPopular"
          :key="movie.id + 1"
          :detail="movie"
        />
      </div>
    </section>

    <!-- Popular Series -->
    <section v-show="listOfMovies.length === 0 && listOfSeries.length === 0">
      <h2>Popular Series</h2>
      <div class="card-expo">
        <CardHome
          @click="movieInfo(serie)"
          v-for="serie in listOfPopSeries"
          :key="serie.id + 1"
          :detail="serie"
        />
      </div>
    </section>

    <!-- movies -->
    <section v-show="listOfMovies.length" class="movies">
      <span
        class="clearResearch"
        @click="clearSearch(listOfMovies)"
        v-show="listOfMovies.length !== 0"
        >Clear Research <i class="fas fa-times"></i
      ></span>
      <h2>Movies</h2>

      <div class="card-expo">
        <Card v-for="movie in listOfMovies" :key="movie.id" :detail="movie" />
      </div>
    </section>
    <!-- series -->
    <section v-show="listOfSeries.length" class="series">
      <span
        class="clearResearch"
        @click="clearSearch(listOfSeries)"
        v-show="listOfSeries.length !== 0"
        >Clear Search <i class="fas fa-times"></i
      ></span>
      <h2>TV Series</h2>

      <div class="card-expo">
        <Card v-for="serie in listOfSeries" :key="serie.id" :detail="serie" />
      </div>
    </section>
  </main>
</template>

<script>
import Card from "@/components/Card";
import CardHome from "@/components/CardHome";
export default {
  name: "Main",
  components: {
    Card,
    CardHome,
  },

  props: {
    listOfMovies: Array,
    listOfSeries: Array,
    listOfPopular: Array,
    listOfPopSeries: Array,
  },

  data() {
    return {
      moviesInfo: [],
    };
  },
  methods: {
    clearSearch(arr) {
      arr.splice(0, arr.length);
    },
  },
};
</script>

<style scoped lang="scss">
@import "@/assets/Styles/Main-style.scss";
</style>
