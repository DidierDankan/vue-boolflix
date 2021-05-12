<template>
  <main>
    <!-- movies -->
    <section v-show="listOfMovies.length" class="movies">
      <h2>Movies</h2>
      <Card v-for="movie in listOfMovies" :key="movie.id" :detail="movie" />
    </section>
    <!-- series -->
    <section v-show="listOfSeries.length" class="series">
      <h2>TV Series</h2>
      <div>
        <Card v-for="serie in listOfSeries" :key="serie.id" :detail="serie" />
      </div>
    </section>
  </main>
</template>

<script>
import Card from "@/components/Card";

export default {
  name: "Main",
  components: {
    Card,
  },

  props: {
    listOfMovies: Array,
    listOfSeries: Array,
  },

  data() {
    return {};
  },
};
</script>

<style scoped lang="scss">
section {
  padding-top: 85px;
}
</style>
