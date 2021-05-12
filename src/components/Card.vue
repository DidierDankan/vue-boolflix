<template>
  <div>
    <!-- movie poster -->
    <div>
      <img
        :src="`https://image.tmdb.org/t/p/w342${detail.poster_path}`"
        :alt="detail.title"
      />

      <!--  movie info -->
      <div>Title: {{ getTitle() }}</div>
      <div v-show="getTitle() !== getOriginalTitle()">
        Original Title:
        {{ getOriginalTitle() }}
      </div>
      <!-- validation for language flag -->
      <div class="langImg">
        <span>Original Language: </span>
        <img
          v-if="getFlag(detail.original_language)"
          :src="require(`@/img/${detail.original_language}.png`)"
          :alt="detail.original_language"
        />
        <span v-else>{{ detail.original_language }}</span>
      </div>
      <!-- vote -->
      <div>
        Vote:
        <span
          v-for="(star, x) in changeNumber(detail.vote_average)"
          :key="x + 10"
        >
          <i class="fas fa-star"></i>
        </span>
        <span
          v-for="(star, i) in 5 - changeNumber(detail.vote_average)"
          :key="i + 100"
        >
          <i class="far fa-star"></i>
        </span>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "Card",
  props: {
    detail: Object,
  },
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
    getTitle() {
      return this.detail.title ? this.detail.title : this.detail.name;
    },
    getOriginalTitle() {
      return this.detail.original_title
        ? this.detail.original_title
        : this.detail.original_name;
    },
  },
};
</script>

<style scoped lang="scss">
.langImg img {
  width: 32px;
}
</style>
