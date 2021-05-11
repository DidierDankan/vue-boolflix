<template>
  <main>
    <section class="movies">
      <p>Movies</p>
      <ul v-for="movie in listOfMovies" :key="movie.id">
        <li>{{ movie.title }}</li>
        <li>{{ movie.original_title }}</li>
        <li v-if="movie.original_language === 'en'">
          <img src="@/img/en.png" :alt="movie.original_language" />
        </li>
        <li v-else-if="movie.original_language === 'it'">
          <img src="@/img/it.png" :alt="movie.original_language" />
        </li>
        <li v-else>{{ movie.original_language }}</li>
        <li>{{ movie.vote_average }}</li>
        <!-- <li>
        <img
          :src="movie.original_language ? './img/en.png' : './img/it.png'"
          alt=""
        />
      </li> -->
      </ul>
    </section>
    <section class="series">
      <p>Series</p>
      <ul v-for="movie in listOfSeries" :key="movie.id">
        <li>{{ movie.name }}</li>
        <li>{{ movie.original_name }}</li>
        <li v-if="movie.original_language === 'en'">
          <img src="@/img/en.png" :alt="movie.original_language" />
        </li>
        <li v-else-if="movie.original_language === 'it'">
          <img src="@/img/it.png" :alt="movie.original_language" />
        </li>
        <li v-else>{{ movie.original_language }}</li>
        <li>{{ movie.vote_average }}</li>
      </ul>
    </section>
  </main>
</template>

<script>
export default {
  // "searchResult"
  name: "Main",
  props: ["listOfMovies", "searchResult", "listOfSeries"],
  data() {
    return {
      //   flags: ["it", "en"],
    };
  },
  methods: {},
};
</script>

<style scoped lang="scss">
ul {
  li {
    img {
      width: 35px;
      height: 20px;
    }
  }
}
</style>
