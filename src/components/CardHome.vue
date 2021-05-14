<template>
  <div>
    <!-- movie poster -->
    <div class="card">
      <img
        class="fix-size-img"
        v-if="detail.poster_path"
        :src="`https://image.tmdb.org/t/p/w185${detail.poster_path}`"
        :alt="detail.title"
      />
      <img
        v-else
        src="https://www.altavod.com/assets/images/poster-placeholder.png"
        alt=""
      />
      <!-- on img hover -->
      <div class="card-info">
        <!--  movie info -->
        <div><span class="bold">Title:</span> {{ getTitle() }}</div>
        <div v-show="getTitle() !== getOriginalTitle()">
          <div>
            <span class="bold">Original Title:</span>
            {{ getOriginalTitle() }}
          </div>
        </div>
        <!-- validation for language flag -->
        <div class="langImg">
          <span class="bold">Original Language: </span>
          <img
            v-if="getFlag(detail.original_language)"
            :src="require(`@/img/${detail.original_language}.png`)"
            :alt="detail.original_language"
          />
          <span v-else>{{ detail.original_language }}</span>
        </div>
        <!-- vote -->
        <div>
          <span class="bold">Vote:</span>
          <span
            class="gold-star"
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
  </div>
</template>

<script>
export default {
  name: "CardHome",
  props: {
    detail: Object,
  },
  data() {
    return {
      flags: ["it", "en"],
    };
  },

  methods: {
    changeNumber(number) {
      return Math.round((number * 5) / 10);
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
@import "@/assets/Styles/CardHome.scss";
</style>
