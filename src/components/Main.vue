<template>
  <main>
    <ul v-for="movie in listOfSearch" :key="movie.id">
      <li>{{ movie.title }}</li>
      <li>{{ movie.original_title }}</li>
      <li v-if="movie.original_language === 'en'">
        <img :src="flagLanguage[0]" :alt="movie.original_language" />
      </li>
      <li v-else-if="movie.original_language === 'it'">
        <img :src="flagLanguage[1]" :alt="movie.original_language" />
      </li>
      <li v-else>{{ movie.original_language }}</li>
      <li>{{ movie.vote_average }}</li>
    </ul>
  </main>
</template>

<script>
export default {
  name: "Main",
  props: ["listOfSearch", "searchResult", "flagLanguage"],
  created() {
    console.log(this.listOfSearch);
  },
  methods: {
    searchMovieSerie() {
      if (
        this.listOfSearch[0].title.toLowerCase().includes(this.searchResult)
      ) {
        return this.listOfSearch;
      }
    },
  },
};
</script>

<style scoped lang="scss"></style>
