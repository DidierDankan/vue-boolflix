<template>
  <div class="profileNav">
    <ul>
      <li>
        <a href="">
          <i class="fas fa-gift"></i>
        </a>
      </li>
      <li>
        <a href="">
          <i class="fas fa-bell"></i>
        </a>
      </li>
    </ul>
    <div class="profile">
      <img src="@/img/avatar_netflix.png" alt="profile_photo" />
    </div>
  </div>
</template>

<script>
export default {
  name: "ProfiloNav",
};
</script>

<style scoped lang="scss">
.profileNav {
  display: flex;
  align-items: center;
  ul {
    display: flex;
    align-items: center;
    list-style: none;
  }
  li {
    margin-right: 30px;
  }
  a {
    text-decoration: none;
    color: #fff;
    font-size: 20px;
  }
  .profile {
    width: 30px;
    height: 30px;
    border-radius: 3px;
    overflow: hidden;
  }
  .profile img {
    width: 100%;
  }
}
</style>
