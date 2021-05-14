<template>
  <header>
    <LogoNavBar />

    <div class="search-box">
      <form class="search">
        <input
          type="search"
          placeholder="Search movies and Tv series"
          v-model.trim="searchText"
        />
        <button
          type="search"
          @click.prevent="$emit('performSearch', searchText)"
        >
          <i class="fas fa-search"></i>
        </button>
      </form>
      <ProfiloNav />
    </div>
  </header>
</template>

<script>
import LogoNavBar from "./LogoNavBar";
import ProfiloNav from "./ProfiloNav";
export default {
  name: "Header",
  components: {
    LogoNavBar,
    ProfiloNav,
  },
  data() {
    return {
      searchText: "",
    };
  },
};
</script>

<style scoped lang="scss">
@import "@/assets/Styles/Header.scss";
</style>
