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
.profileNav {
  display: flex;
  align-items: center;
  .navProfile-ul {
    display: flex;
    align-items: center;
    list-style: none;
    li {
      margin-right: 30px;
    }
    a {
      text-decoration: none;
      color: #fff;
      font-size: 20px;
    }
  }
  .profile {
    position: relative;
    width: 30px;
    height: 30px;
    border-radius: 3px;
    cursor: pointer;
    &:hover .arrow {
      transform: rotate(180deg);
    }
    .arrow {
      position: absolute;
      left: 110%;
      top: 50%;
      width: 0;
      height: 0;
      background: transparent;
      border-top: 5px solid #fff;
      border-right: 5px solid transparent;
      border-left: 5px solid transparent;
      transition: transform 0.2s;
    }
  }
  .profile img {
    width: 100%;
    border-radius: 3px;
  }
  .profile:hover .drop-down-profile {
    visibility: visible;
  }
  //on hover in profile
  .arrow-box {
    position: absolute;
    bottom: 100%;
    right: 17px;
    width: 0;
    height: 0;
    background: transparent;
    border-bottom: 10px solid #fff;
    border-right: 10px solid transparent;
    border-left: 10px solid transparent;
  }
  .drop-down-profile {
    visibility: hidden;
    position: absolute;
    top: 165%;
    left: -355%;
    width: 150px;
    padding: 10px;
    background: #0e0e0ece;
    transition: visibility 0.3s;
    border: 1px solid rgba(238, 238, 238, 0.671);
    .drop-down-ul {
      list-style: none;
      display: flex;
      flex-direction: column;

      border-bottom: 1px solid #fff;
      a {
        margin-bottom: 5px;
        text-decoration: none;
        font-size: 0.8rem;
        color: #fff;
        &:hover {
          text-decoration: underline;
        }
      }
    }
  }

  .underline-box {
    cursor: pointer;
    display: flex;
    align-items: center;
    margin-bottom: 10px;
    &:hover span {
      text-decoration: underline;
    }
    span {
      font-size: 0.8rem;
      color: #fff;
      margin-left: 10px;
    }
  }

  .img-box {
    width: 30px;
    height: 30px;
    border-radius: 3px;

    img {
      width: 100%;
    }
  }

  .account {
    margin-top: 10px;
    .account-ul {
      list-style: none;
      .account-manage {
        margin-bottom: 5px;
        a {
          text-decoration: none;
          color: #fff;
          font-size: 0.8rem;

          &:hover {
            text-decoration: underline;
          }
        }
      }
    }
  }
}
</style>
