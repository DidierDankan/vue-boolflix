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
header {
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 0px 65px;
  height: 70px;
  background: #0e0e0ece;
  z-index: 1;
}
.search-box {
  width: 45%;
  display: flex;
  align-items: center;
  justify-content: space-between;
  .search {
    display: flex;
    align-items: center;
    height: 25px;
    width: 230px;
    background: transparent;
    cursor: pointer;

    input {
      display: flex;
      margin-left: 5px;
      width: 200px;
      border: none;
      padding: 4px;
      background: #fff;
      text-overflow: ellipsis;
      overflow: hidden;
      animation: search 0.3s linear;
      outline: none;
      transition: border 0.1s;
      &:focus {
        border: 2px solid #d91a28;
      }
    }
  }
}

button {
  border: none;
  background: transparent;
  padding: 5px 10px;
  cursor: pointer;
}

i {
  font-size: 18px;
  color: #fff;
}
</style>
