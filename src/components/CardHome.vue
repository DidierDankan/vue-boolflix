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
@import "@/assets/Styles/Variabile.scss";
.card {
  position: relative;
  width: 185px;
  margin: 5px;
  border-radius: 5px;
  filter: drop-shadow(3px 0px 3px #444141a8);
  overflow: hidden;
  cursor: pointer;

  &:hover .card-info {
    visibility: visible;
  }
  .fix-size-img {
    object-fit: contain;
    object-position: bottom;
  }
}

.card-info {
  display: $flex;
  flex-direction: column;
  justify-content: center;
  position: absolute;
  top: 0;
  right: 0;
  left: 0;
  bottom: 0;
  padding: 10px;
  color: #fff;
  font-size: 0.8rem;
  background: #0e0e0eb0;
  visibility: hidden;
  transition: visibility 0.2s;
  & > div {
    margin-bottom: 5px;
  }
}

.bold {
  font-weight: 600;
}

.gold-star {
  color: rgba(228, 176, 5, 0.904);
}

.langImg img {
  width: 32px;
}
</style>
