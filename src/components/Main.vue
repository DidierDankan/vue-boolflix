<template>
  <main>
    <div>
      <!-- popular movies -->
      <section v-show="listOfMovies.length === 0 && listOfSeries.length === 0">
        <h2>Popular Movies</h2>
        <div class="card-expo">
          <CardHome
            @click="movieInfo(index)"
            v-for="(movie, index) in listOfPopular"
            :key="movie.id + 1"
            :detail="movie"
          />
        </div>
      </section>
    </div>
    <!-- Popular Series -->
    <section v-show="listOfMovies.length === 0 && listOfSeries.length === 0">
      <h2>Popular Series</h2>
      <div class="card-expo">
        <CardHome
          @click="movieInfo(index)"
          v-for="(serie, index) in listOfPopSeries"
          :key="serie.id + 1"
          :detail="serie"
        />
      </div>
    </section>
    <!-- movies -->
    <section v-show="listOfMovies.length" class="movies">
      <span
        class="clearResearch"
        @click="clearSearch(listOfMovies)"
        v-show="listOfMovies.length !== 0"
        >Clear Research <i class="fas fa-times"></i
      ></span>
      <h2>Movies</h2>

      <div class="card-expo">
        <Card v-for="movie in listOfMovies" :key="movie.id" :detail="movie" />
      </div>
    </section>
    <!-- series -->
    <section v-show="listOfSeries.length" class="series">
      <span
        class="clearResearch"
        @click="clearSearch(listOfSeries)"
        v-show="listOfSeries.length !== 0"
        >Clear Search <i class="fas fa-times"></i
      ></span>
      <h2>TV Series</h2>

      <div class="card-expo">
        <Card v-for="serie in listOfSeries" :key="serie.id" :detail="serie" />
      </div>
    </section>
  </main>
</template>

<script>
import Card from "@/components/Card";
import CardHome from "@/components/CardHome";

export default {
  name: "Main",
  components: {
    Card,
    CardHome,
  },

  props: {
    listOfMovies: Array,
    listOfSeries: Array,
    listOfPopular: Array,
    listOfPopSeries: Array,
  },

  data() {
    return {
      moviesInfo: [],
    };
  },
  methods: {
    clearSearch(arr) {
      arr.splice(0, arr.length);
    },
    movieInfo(index) {
      this.moviesInfo.push(this.listOfMovies[index]);
      console.log(this.listOfMovies[index]);
    },
  },
};
</script>

<style scoped lang="scss">
main {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  padding-top: 170px;
  height: 100vh;
  overflow: auto;
  background-image: linear-gradient(180deg, #1a1818, #110b0a);
  h2 {
    margin-top: 10px;
    margin-bottom: 10px;
    color: #fff;
  }
}
.movies {
  position: relative;
  .clearResearch {
    position: absolute;
    right: 10px;
    top: 0;
    color: #7a120c;
    font-size: 1.2rem;
    i {
      cursor: pointer;
    }
  }
}
.series {
  position: relative;
  padding-bottom: 10px;
  .clearResearch {
    position: absolute;
    right: 10px;
    top: 0;
    color: #7a120c;
    font-size: 1.2rem;
    i {
      cursor: pointer;
    }
  }
}

.card-expo {
  display: flex;
  justify-content: flex-start;
  padding: 0 5px;
  width: calc(98vw - 5px);
  overflow-x: scroll;
}
</style>
