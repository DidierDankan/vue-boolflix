<template>
  <main>
    <!-- movies -->
    <section class="movies">
      <p>Movies</p>
      <ul v-for="movie in listOfMovies" :key="movie.id">
        <!-- movie poster -->
        <img
          :src="`https://image.tmdb.org/t/p/w342${movie.poster_path}`"
          :alt="movie.title"
        />
        <!--  movie info -->
        <li>Title: {{ movie.title }}</li>
        <li>Original Title: {{ movie.original_title }}</li>
        <!-- validation for language flag -->
        <li v-if="movie.original_language === 'en'">
          <span>Original Language: </span
          ><img src="@/img/en.png" :alt="movie.original_language" />
        </li>
        <li v-else-if="movie.original_language === 'it'">
          <span>Original Language: </span
          ><img src="@/img/it.png" :alt="movie.original_language" />
        </li>
        <li v-else>{{ movie.original_language }}</li>
        <!-- vote -->
        <li>
          Vote: {{ changeNumber(movie.vote_average) }}
          <i class="fas fa-star"></i>
          <i class="far fa-star"></i>
        </li>
      </ul>
    </section>
    <!-- series -->
    <section class="series">
      <p>Series</p>
      <ul v-for="serie in listOfSeries" :key="serie.id">
        <!-- serie poster -->
        <img
          :src="`https://image.tmdb.org/t/p/w342${serie.poster_path}`"
          :alt="serie.title"
        />
        <!-- series info -->
        <li>{{ serie.name }}</li>
        <li>{{ serie.original_name }}</li>
        <!-- validation for language flag -->
        <li v-if="serie.original_language === 'en'">
          <span>Original Language: </span
          ><img src="@/img/en.png" :alt="serie.original_language" />
        </li>
        <li v-else-if="serie.original_language === 'it'">
          <span>Original Language: </span
          ><img src="@/img/it.png" :alt="serie.original_language" />
        </li>
        <li v-else>{{ serie.original_language }}</li>
        <!-- vote -->
        <li>
          Vote: {{ changeNumber(serie.vote_average) }}
          <span>
            <i class="fas fa-star"></i>
            <i class="far fa-star"></i
          ></span>
        </li>
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
    return {};
  },
  methods: {
    changeNumber(number) {
      return Math.round((number * 5) / 10);
    },
  },
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
