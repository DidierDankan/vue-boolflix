<template>
  <header>
    <a href="http://localhost:8080/"
      ><img
        src="https://fontmeme.com/permalink/210510/7fdf6fbd9857bafc3f5bb63abad2261f.png"
        alt="gunplay-font"
        border="0"
    /></a>

    <form class="search">
      <button type="search" @click.prevent="$emit('performSearch', searchText)">
        Search
      </button>
      <input
        type="search"
        placeholder="Search movies and Tv series"
        v-model.trim="searchText"
      />
    </form>
  </header>
</template>

<script>
export default {
  name: "Header",
  data() {
    return {
      searchText: "",
    };
  },
};
</script>

<style scoped lang="scss">
header {
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 5px 15px;
  height: 55px;
  img {
    height: 50px;
  }
  .search {
    width: 50%;
    display: flex;
    align-items: center;
    justify-content: right;
    input {
      text-overflow: ellipsis;
      overflow: hidden;
    }
  }
}
</style>
