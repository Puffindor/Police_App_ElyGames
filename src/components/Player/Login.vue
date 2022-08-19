<template>
  <div class="login">
    <div class="pic2">
      <login_pic2 />
    </div>
    <div class="wrapper">
      <img src="@/Assets/logo_login.png" />
      <div class="login_container">
        <input placeholder="Nom Prénom..." v-model="this.login" />
      </div>
      <div class="password_container">
        <input placeholder="identifiant..." v-model="this.password" />
        <button @click="Login" class="enter"></button>
      </div>
    </div>
    <div class="pic1">
      <login_pic1 />
    </div>
  </div>
</template>

<script>
import Login_pic1 from "@/Assets/login_pic1.vue";
import Login_pic2 from "@/Assets/login_pic2.vue";
export default {
  emits: ["cl"],
  components: { Login_pic1, Login_pic2 },
  props: ["PlayerProfile"],

  data() {
    return {
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
  },
};
</script>

<style scoped>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

.pic1 {
  transform: translateX(390px);
}
.pic2 {
  transform: translateX(-390px);
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
</style>
