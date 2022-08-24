<template>
  <span>{{ login_pics() }}</span>
  <div class="login">
    <img :src="this.pic1" class="pic1" />

    <div class="wrapper">
      <img src="@/Assets/logo_login.png" />
      <div class="login_container">
        <input placeholder="Nom Prénom..." v-model="this.login" />
      </div>
      <div class="password_container">
        <input placeholder="identifiant..." v-model="this.password" />
        <button @click="Login" class="enter"><Icon_login /></button>
      </div>
    </div>

    <img :src="this.pic2" class="pic2" />
  </div>
</template>

<script>
import Icon_login from "@/Assets/icons/Icon_login.vue";
export default {
  emits: ["cl"],
  components: { Icon_login },
  props: ["PlayerProfile"],

  data() {
    return {
      pic1: "",
      pic2: "",
      login: "",
      password: "",
    };
  },
  methods: {
    Login() {
      if (
        this.login === this.PlayerProfile.login &&
        this.password === this.PlayerProfile.password
      ) {
        this.$emit("cl", 1);
      } else {
        this.login = "";
        this.password = "";
      }
    },
    login_pics() {
      switch (window.screen.width) {
        case 1400:
          this.pic1 = require("@/Assets/login_pic1_small.png");
          this.pic2 = require("@/Assets/login_pic2_small.png");
          break;
        default:
          this.pic1 = require("@/Assets/logo_login_left.png");
          this.pic2 = require("@/Assets/logo_login_right.png");
          break;
      }
    },
  },
  computed: {},
};
</script>

<style scoped>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

.pic1 {
  transform: translateX(-390px);
}
.pic2 {
  transform: translateX(390px);
}

input {
  font-family: "Segoe UI";
  font-size: 16px;
  font-weight: 500;
  outline: none;
  background-color: transparent;
  border-style: hidden;
}

.wrapper {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}
.enter {
  display: flex;
  justify-content: center;
  align-items: center;
  cursor: pointer;
  width: 48px;
  height: 48px;
  background-color: #396aff;
  border-style: hidden;
}
.password_container {
  margin-top: 15px;

  display: flex;
  justify-content: space-between;
  align-items: center;
  padding-left: 14px;
  width: 310px;
  height: 48px;
  background-color: #ffffff;
}
.login_container {
  margin-top: 60px;
  display: flex;
  justify-content: flex-start;
  align-items: center;
  padding-left: 14px;
  width: 310px;
  height: 48px;
  background-color: #ffffff;
}
.login {
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: row;
  position: fixed;

  width: 100%;
  height: 100%;

  background: radial-gradient(closest-side, #013c6c, #032a48);
}
@media screen and (max-width: 1401px) {
  .pic1 {
    transform: translateX(-50px);
  }
  .pic2 {
    transform: translateX(50px);
  }
}
@media screen and (min-width: 2047px) {
}
@media screen and (min-width: 2559px) {
  .pic1 {
    transform: translateX(-590px);
  }
  .pic2 {
    transform: translateX(590px);
  }
}

@media screen and (min-width: 3839px) {
  .pic1 {
    transform: translateX(-1200px);
  }
  .pic2 {
    transform: translateX(1200px);
  }
}
</style>
