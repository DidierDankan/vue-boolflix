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
        <li>
          <span>Original Language: </span>
          <img
            v-if="getFlag(movie.original_language)"
            :src="require(`@/img/${movie.original_language}.png`)"
            :alt="movie.original_language"
          />
          <span v-else>{{ movie.original_language }}</span>
        </li>
        <!-- vote -->
        <li>
          Vote:
          <span
            v-for="(star, x) in changeNumber(movie.vote_average)"
            :key="x + 10"
          >
            <i class="fas fa-star"></i>
          </span>
          <span
            v-for="(star, i) in 5 - changeNumber(movie.vote_average)"
            :key="i + 100"
          >
            <i class="far fa-star"></i>
          </span>
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
        <li>
          <span>Original Language: </span>
          <img
            v-if="getFlag(serie.original_language)"
            :src="require(`@/img/${serie.original_language}.png`)"
            :alt="serie.original_language"
          />
          <span v-else>{{ serie.original_language }}</span>
        </li>

        <li>
          Vote:
          <span
            v-for="(star, x) in changeNumber(serie.vote_average)"
            :key="x + 10"
          >
            <i class="fas fa-star"></i>
          </span>
          <span
            v-for="(star, i) in 5 - changeNumber(serie.vote_average)"
            :key="i + 100"
          >
            <i class="far fa-star"></i>
          </span>
        </li>
      </ul>
    </section>
  </main>
</template>

<script>
export default {
  // "searchResult"
  name: "Main",
  props: ["listOfMovies", "listOfSeries"],

  data() {
    return {
      qualityStars: "",
      flags: ["it", "en"],
    };
  },
  methods: {
    changeNumber(number) {
      return Math.round((number * 5) / 10);
    },
    getStars() {
      this.qualityStars = this.changeNumber(this.serie.vote_average);
    },
    getFlag(lang) {
      return this.flags.includes(lang);
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
