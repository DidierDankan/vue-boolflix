<template>
  <main>
    <!-- popular movies -->
    <!-- movies -->
    <section v-show="listOfMovies.length" class="movies">
      <h2>Movies</h2>
      <div class="card-expo">
        <Card v-for="movie in listOfMovies" :key="movie.id" :detail="movie" />
      </div>
    </section>
    <!-- series -->
    <section v-show="listOfSeries.length" class="series">
      <h2>TV Series</h2>

      <div class="card-expo">
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
    listOfPopular: Array,
  },

  data() {
    return {};
  },
};
</script>

<style scoped lang="scss">
main {
  padding-top: 85px;
  height: 100vh;
  overflow: auto;
  background-image: linear-gradient(180deg, #1a1818, #110b0a);
  h2 {
    color: #fff;
  }
}

.card-expo {
  display: flex;
  justify-content: start;
}
</style>
