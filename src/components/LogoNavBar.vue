<template>
  <div class="nav">
    <a href="https://fontmeme.com/netflix-font/"
      ><img
        src="https://fontmeme.com/permalink/210512/569a01fdb501fcbdb363a8d9dad90c4f.png"
        alt="netflix-font"
        border="0"
    /></a>
    <div>
      <ul class="navBar">
        <li v-for="(link, index) in navBar" :key="index">
          <a :href="link.url"> {{ link.door }} </a>
        </li>
      </ul>
    </div>
  </div>
</template>

<script>
export default {
  name: "LogoNavBar",
  data() {
    return {
      navBar: [
        {
          door: "Home",
          url: "/home",
        },
        {
          door: "TV Shows",
          url: "/TVshows",
        },
        {
          door: "Movies",
          url: "/movies",
        },
        {
          door: "New & Popular",
          url: "/new&popular",
        },
        {
          door: "My List",
          url: "/mylist",
        },
      ],
    };
  },
};
</script>

<style scoped lang="scss">
img {
  display: flex;
  height: 40px;
}
.nav {
  display: flex;
  align-items: center;
}

.navBar {
  display: flex;
  list-style: none;
  li {
    a {
      margin-left: 20px;
      color: #fff;
      text-decoration: none;
      font-size: 14px;
      transition: color 0.4s;
      &:hover {
        color: #4b5a6b;
      }
    }
  }
}
</style>
