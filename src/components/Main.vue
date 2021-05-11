<template>
  <main>
    <ul v-for="movie in listOfSearch" :key="movie.id">
      <li>{{ movie.title }}</li>
      <li>{{ movie.original_title }}</li>
      <li v-if="movie.original_language === 'en'">
        <img src="@/img/en.png" alt="" />
      </li>
      <li v-else-if="movie.original_language === 'it'">
        <img src="@/img/it.png" alt="" />
      </li>
      <li v-else>{{ movie.original_language }}</li>
      <!-- <li>
        <img :src="movie.original_language ? flags[0] : flags[1]" alt="" />
      </li> -->
      <li>{{ movie.vote_average }}</li>
    </ul>
  </main>
</template>

<script>
export default {
  // "searchResult"
  name: "Main",
  props: ["listOfSearch"],
  data() {
    return {
      //   flags: ["it", "en"],
    };
  },
  methods: {},
  //     searchMovieSerie() {
  //       if (this.listOfSearch[0].title.toLowerCase() === this.searchResult) {
  //         return this.listOfSearch;
  //       }
  //     },
  //   },
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
