<template>
  <div class="UpperPlate">
    <div class="logo_container">
      <Logo_header :logo_size="LogoSize" :viewBox="viewBox" />
      <strong class="logo_string"> L.S.P.D </strong>
    </div>
    <div class="search">
      <Icon_seacrh :size="IconSize" @click="OpenSearch" />
      <span class="string"> Search </span>
      <input
        @input="this.SearchInput = $event.target.value"
        v-bind:value="this.SearchInput"
        class="input"
        placeholder="by name of phone"
      />
    </div>
    <div @click="Show" class="player">
      <div>
        <img :src="img" class="img" />
        <div class="status_indicator"></div>
      </div>
      <span class="name">{{ this.PlayerProfile.name }}</span>
      <span class="rank">{{ this.PlayerProfile.rank }}</span>
    </div>
  </div>
  <div class="popup1" v-if="ShowModal">
    <div class="modal">
      <div @click="Staus(1)" class="state">
        <div class="status1"></div>
        Need a parthner
      </div>
      <div class="state" @click="Staus(2)">
        <div class="status2"></div>
        AFK
      </div>
      <div class="disturb" @click="Staus(3)">
        <div class="status3"></div>
        Do not disturb
        <span class="desc"
          >You will not receive notifications about invites</span
        >
      </div>
      <div class="disturb" @click="Staus(4)">
        <div class="status4"></div>
        On duty
        <span class="desc"
          >You get this status when you accept the invitation</span
        >
      </div>
      <div class="profile" @click="Profile">
        <Icon_profile style="margin-right: 13px" />My profile
      </div>
    </div>
  </div>
</template>

<script>
import Icon_seacrh from "../../Assets/icons/Icon_seacrh.vue";
import Icon_profile from "../../Assets/icons/Icon_profile.vue";
import Logo_header from "../../Assets/icons/Logo_header.vue";
export default {
  emits: ["cl", "status", "search"],
  props: ["PlayerProfile"],
  components: { Icon_seacrh, Icon_profile, Logo_header },
  data() {
    return {
      avatar: "",
      SearchInput: "",
      ShowModal: false,
      viewBox: "0 0 72 72",
    };
  },
  input: "",
  methods: {
    Profile() {
      this.$emit("cl", 10);
      this.ShowModal = false;
    },
    Staus(id) {
      this.$emit("status", id);
      this.ShowModal = false;
    },
    Show() {
      this.ShowModal = !this.ShowModal;
    },
    OpenSearch() {
      if (this.SearchInput) {
        this.$emit("search", this.SearchInput);

        this.$emit("cl", 7);
        this.SearchInput = "";
      }
    },
  },
  computed: {
    IconSize() {
      if (window.screen.width > 3839) {
        return 45;
      } else {
        return 26;
      }
    },
    LogoSize() {
      if (window.screen.width > 3839) {
        this.viewBox = "0 0 200 200";
        return 200;
      } else {
        this.viewBox = "0 0 72 72";
        return 72;
      }
    },
    img() {
      if (this.PlayerProfile.avatar) {
        return (this.avatar = this.PlayerProfile.avatar);
      } else {
        return (this.avatar = require("../../Assets/icons/base_avatar.png"));
      }
    },
    Color() {
      switch (this.PlayerProfile.status) {
        case "AFK":
          return "#F6B73E";

        case "On duty":
          return "#396AFF";

        case "Do not disturb":
          return "#E53F3F";

        case "Need a parthner":
          return "#00BC7E";
      }
    },
  },
};
</script>

<style scoped>
@import url("https://fonts.googleapis.com/css?family=Roboto+Condensed");
@import url("https://fonts.googleapis.com/css2?family=Montserrat:ital,wght@1,600&display=swap");

strong {
  font-family: "Roboto", sans-serif;
  color: white;
}

.disturb {
  cursor: default;

  border-radius: 6px;
  padding-top: 10px;
  font-family: "Segoe UI";
  font-size: 16px;
  font-weight: 500;
  height: 70px;
  flex-wrap: wrap;
  display: flex;
  align-items: center;
}
.disturb:hover {
  font-family: "Segoe UI";
  font-size: 16px;
  font-weight: 500;
  height: 70px;
  flex-wrap: wrap;
  display: flex;
  background-color: #f0f3f9;
}
.desc {
  font-family: "Segoe UI";
  font-size: 12px;
  font-weight: 500;
  color: #a1acc0;
  width: 177px;
  margin-left: 51px;
}
.profile {
  cursor: default;
  width: 236px;

  height: 55px;
  display: flex;
  justify-content: flex-start;
  align-items: center;
  font-family: "Segoe UI";
  font-size: 16px;
  font-weight: 500;
  border-top: 1px solid #eff1f9;
  margin-top: 8px;
  padding-left: 6px;
}
.profile:hover {
  cursor: default;
  width: 236px;

  height: 55px;
  display: flex;
  justify-content: flex-start;
  align-items: center;
  font-family: "Segoe UI";
  font-size: 16px;
  font-weight: 500;
  border-top: 1px solid #eff1f9;
  margin-top: 8px;
  background-color: #f0f3f9;
  border-radius: 6px;
  padding-left: 6px;
}
.state {
  flex-wrap: wrap;
  cursor: default;
  min-height: 35px;
  max-height: 80px;
  border-radius: 6px;
  display: flex;
  margin-top: 6px;
  font-family: "Segoe UI";
  font-size: 16px;
  font-weight: 500;
  align-items: center;
}
.state:hover {
  height: 35px;
  border-radius: 6px;
  display: flex;
  margin-top: 6px;
  font-family: "Segoe UI";
  font-size: 16px;
  font-weight: 500;
  align-items: center;

  background-color: #f0f3f9;
  transition: 0.3s;
}
.modal {
  padding-left: 10px;
  padding-right: 10px;
  justify-content: flex-start;
  position: fixed;
  margin-left: 1550px;
  margin-bottom: 200px;
  z-index: 100;
  display: flex;
  flex-direction: column;
  margin-top: 20px;
  width: 271px;
  height: 306px;
  border-radius: 4px;
  background-color: white;
  z-index: 10000;
}

.img {
  width: 73px;
  height: 73px;
  border-radius: 60px;
  grid-area: img;
}

.status1 {
  margin-left: 10px;
  margin-right: 16px;
  width: 15px;
  height: 15px;
  background-color: #00bc7e;
  border-radius: 15px;
}
.status2 {
  margin-left: 10px;
  margin-right: 16px;
  width: 15px;
  height: 15px;
  background-color: #f6b73e;
  border-radius: 15px;
}
.status3 {
  margin-left: 10px;
  margin-right: 16px;
  width: 15px;
  height: 15px;
  background-color: #e13c3c;
  border-radius: 15px;
}
.status4 {
  margin-left: 10px;
  margin-right: 16px;
  width: 15px;
  height: 15px;
  background-color: #396aff;
  border-radius: 15px;
}

.status_indicator {
  width: 15px;
  height: 15px;
  background-color: v-bind(Color);
  border-radius: 15px;
  z-index: 100;
  margin-left: 55px;
  transform: translateY(-20px);
}
.name {
  grid-area: name;
  align-self: end;
}
.rank {
  color: #5e6165;
  grid-area: rank;
}
.player {
  cursor: pointer;
  margin-left: 45vw;
  font-family: "Segoe UI";
  font-weight: 600;
  font-size: 20px;
  display: grid;
  color: white;
  grid-template-columns: 73px 200px;
  grid-template-rows: 36px 36px;
  column-gap: 22px;
  grid-template-areas: "img name" "img rank";
}
.input {
  color: white;
  font-size: 22px;
  background-color: transparent;
  border-style: hidden;
  outline: none;
}

.search {
  font-weight: 600;
  font-family: "Segoe UI";
  margin-left: 41px;
  display: grid;
  grid-template-columns: 54px 77px 190px;
  align-items: end;
}

.string {
  font-family: "Segoe UI";
  font-size: 22px;
  color: #ffffff;
}

.logo_string {
  margin-right: 42px;
}

.logo_container {
  font-size: 41px;
  justify-content: space-around;
  width: 300px;
  display: flex;
  align-items: center;
  border-right: solid 1px #1f2632;
}

.UpperPlate {
  display: flex;
  align-items: center;
  width: 100vw;
  height: 115px;
  background-color: #121924;
  z-index: 10;
}

@media screen and (max-width: 1401px) {
  .modal {
    margin-top: 150px;
    margin-left: 1000px;
  }
  .player {
    margin-left: 420px;
  }
  .UpperPlate {
    position: absolute;
    left: 0;
  }
}

@media screen and (min-width: 2047px) {
  .player {
    margin-left: 1000px;
  }
  .modal {
    margin-left: 1700px;
  }
}
@media screen and (min-width: 2559px) {
  .player {
    margin-left: 1600px;
  }
  .modal {
    margin-left: 2200px;
  }
}

@media screen and (min-width: 3839px) {
  .UpperPlate {
    height: 200px;
  }
  .string {
    font-size: 40px;
  }
  .input {
    width: 400px;
    font-size: 38px;
  }
  .search {
    grid-template-columns: 100px 150px 190px;
  }
  .logo_string {
    font-size: 60px;
  }

  .logo_container {
    font-size: 41px;
    justify-content: space-around;
    width: 400px;
    display: flex;
    align-items: center;
    border-right: solid 1px #1f2632;
  }
  .logo_string {
    margin-left: 20px;
  }
  .modal {
    margin-left: 3300px;
  }
  .img {
    width: 100px;
    height: 100px;
    margin-top: 60px;
  }
  .name {
    font-size: 40px;
  }
  .rank {
    font-size: 40px;
  }
  .player {
    grid-template-columns: 100px 300px;
    grid-template-rows: 100px 100px;
    margin-left: 2400px;
  }
  .status_indicator {
    width: 20px;
    height: 20px;

    margin-left: 70px;
    transform: translateY(-25px);
  }
}
</style>
