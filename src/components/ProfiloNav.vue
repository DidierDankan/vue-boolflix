<template>
  <div class="profileNav">
    <ul class="navProfile-ul">
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
      <img :src="profiles[indexDinamico].avatar" :alt="profiles.name" />
      <div class="arrow"></div>
      <!-- on hover -->
      <div class="drop-down-profile">
        <!-- small arrow box -->
        <div class="arrow-box"></div>
        <!-- drop down info -->
        <ul class="drop-down-ul">
          <li
            class="underline-box"
            v-for="(profile, index) in profiles"
            :key="index"
            @click="onSelectProfile(index)"
          >
            <div class="img-box">
              <img :src="profile.avatar" :alt="profile.name" />
            </div>
            <span>{{ profile.name }}</span>
          </li>
          <a href="/manageProfile">Manage Profile</a>
        </ul>
        <div class="account">
          <ul class="account-ul">
            <li class="account-manage"><a href="/Account">Account</a></li>
            <li class="account-manage">
              <a href="/HelpCenter">Help Center</a>
            </li>
            <li class="account-manage">
              <a href="/SignOut">Sign out of Netflix</a>
            </li>
          </ul>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "ProfiloNav",
  data() {
    return {
      profiles: [
        {
          name: "Profilo-1",
          avatar: require("@/img/avatar_netflix.png"),
          visible: true,
        },
        {
          name: "Profilo-2",
          avatar: require("@/img/avatar2.png"),
          visible: true,
        },
        {
          name: "Profilo-3",
          avatar: require("@/img/avatar3.png"),
          visible: true,
        },
        {
          name: "Profilo-4",
          avatar: require("@/img/avatar4.png"),
          visible: true,
        },
      ],
      indexDinamico: 0,
    };
  },
  methods: {
    onSelectProfile(index) {
      this.indexDinamico = index;
    },
  },
};
</script>

<style scoped lang="scss">
@import "@/assets/Styles/Variabile.scss";
@import "@/assets/Styles/Profilo-nav.scss";
</style>
