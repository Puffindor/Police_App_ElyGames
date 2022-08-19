<template>
  <div>
    <span>{{ Invited() }}</span>
    <h1 class="head">Police Profile</h1>
    <span>{{ Color() }}</span>
    <div class="profile">
      <div class="case_history">
        <h2>Cases History</h2>
        <div class="list_head">
          <span>Name case</span>
          <span>Status</span>
        </div>
        <div class="list_container1">
          <div v-for="crime in this.agent_profile.history" class="list_item1">
            <Agent_profile_list :name="crime.name" :status="crime.status" />
          </div>
        </div>
      </div>
      <div class="rank_container"></div>
      <div class="medals">
        <div class="medals_head">Medals</div>
        <Medals_list :Medals="this.agent_profile.medals" />
      </div>
      <div class="left_column">
        <div class="img_container">
          <img class="img" :src="img" />

          <button @click="Invite1" class="btn2">{{ this.invite }}</button>
        </div>
        <div class="name_container">
          <span class="name">{{ this.agent_profile.name }}</span>
          <span class="status_container">
            {{ this.agent_profile.status }}
          </span>
          <span class="rank">{{ this.agent_profile.rank }}</span>
        </div>
        <div class="info_container">
          <span class="b"
            ><span class="h">Birthday: </span
            >{{ this.agent_profile.birthday }}</span
          >
          <span class="b"
            ><span class="h">Id: </span>{{ this.agent_profile.id }}</span
          >
          <span class="b"
            ><span class="h">Phone: </span>{{ this.agent_profile.phone }}</span
          >
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import Medals_list from "@/components/Player/Medals_list.vue";
import Agent_profile_list from "./Agent_profile_list.vue";
export default {
  emits: ["invited"],
  props: ["agent_profile"],
  data() {
    return {
      color: "#396aff",
      btn_color: "#396aff",
      btn_color_hover: "#7899FF",
      invite: "Invite",
      avatar: "",
      base_avatar: "./icons/base_avatar.png",
    };
  },
  methods: {
    Invite1() {
      this.$emit("invited", this.agent_profile.id);
    },
    Invited() {
      if (this.agent_profile.invited === true) {
        this.invite = "Invite send";
        this.btn_color = "#E0E7EF";
        this.btn_color_hover = "#E0E7EF";
      }
    },

    Color() {
      switch (this.agent_profile.status) {
        case "AFK":
          this.color = "#F6B73E";
          break;
        case "On duty":
          this.color = "#396AFF";
          break;
        case "Do not disturb":
          this.color = "#E53F3F";
          break;
        case "Need a parthner":
          this.color = "#00BC7E";
          break;
      }
    },
  },
  computed: {
    img() {
      if (this.agent_profile.avatar) {
        return (this.avatar = this.agent_profile.avatar);
      } else {
        return (this.avatar = require("@/Assets/icons/base_avatar.png"));
      }
    },
  },

  components: { Medals_list, Agent_profile_list },
};
</script>

<style scoped>
@import url("https://fonts.googleapis.com/css2?family=Montserrat:wght@700&display=swap");

::-webkit-scrollbar {
  width: 5px;
}
::-webkit-scrollbar-track {
  width: 5px;
}

::-webkit-scrollbar-thumb {
  background-color: #396aff;
  border-radius: 10px;
}
.list_container1 {
  width: 570px;
  max-height: 400px;
  overflow: auto;
  display: flex;
  justify-content: flex-start;
  flex-wrap: wrap;
}

.medals_head {
  font-family: Arial, Helvetica, sans-serif;
  font-size: 28px;
  font-weight: 700;
  margin-top: 25px;
  margin-bottom: 22px;
  margin-left: 649px;
}
.list_item1 {
  justify-items: end;
  font-family: Arial;
  font-size: 18px;
  font-weight: 700;
  display: grid;
  align-items: center;
  grid-template-columns: 366px 149px;
  margin-left: 40px;
  height: 80px;
  border-bottom: #c6cddf solid 1px;
  width: 505px;
}
.list_head {
  display: grid;
  grid-template-columns: 398px 117px;
  font-family: "Segoe UI";
  font-size: 18px;
  font-weight: 600;
  color: #a1acc0;
  margin-left: 40px;
  margin-top: 25px;
  margin-bottom: 40px;
}

h2 {
  font-family: Arial;
  font-size: 28px;
  font-weight: 700;
  margin-left: 199px;
  margin-top: 26px;
}
.profile {
  margin-left: 114px;
  display: grid;
  column-gap: 19px;
  row-gap: 20px;
  grid-template-columns: 788px 585px;
  grid-template-rows: 281px 264px 238px;
  grid-template-areas: "name history" "rank history" "medals medals";
}
.medals {
  grid-area: medals;
  width: 1392px;
  height: 238px;
  border-radius: 4px;
  background-color: white;
}
.rank_container {
  grid-area: rank;
  width: 788px;
  height: 264px;
  border-radius: 4px;
  background-color: white;
}
.case_history {
  grid-area: history;
  width: 585px;
  height: 566px;
  border-radius: 4px;
  background-color: white;
}

.left_column {
  grid-area: name;
  display: grid;
  width: 788px;
  height: 281px;
  border-radius: 4px;
  grid-template-columns: 206px 1fr;
  grid-template-rows: repeat(2, 1fr);
  column-gap: 26px;
  grid-template-areas: "img name" "img info";
  background-color: #ffffff;
}

.img {
  width: 181px;
  height: 181px;
  margin-top: 25px;
  margin-left: 25px;
}

.b {
  font-family: Arial;
  font-size: 18px;
  font-weight: 500;
}
.h {
  font-family: Arial;
  font-size: 18px;
  font-weight: 700;
}
.status_container {
  border-radius: 4px;
  font-family: Arial;
  font-size: 18px;
  font-weight: 700;
  color: v-bind(color);
  justify-self: end;
}
.rank {
  font-family: "Segoe UI";
  font-size: 20px;
  color: #a1acc0;
  font-weight: 600;
  margin-bottom: 20px;
}
.name {
  font-family: "Segoe UI";
  font-size: 28px;
  color: #253042;
  font-weight: 700;
}

.name_container {
  align-items: center;
  justify-items: start;
  width: 531px;
  height: 90px;
  border-bottom: solid 1px #c6cddf;
  display: grid;
  grid-template-columns: 201px 1fr;

  margin-top: 25px;
  grid-area: name;
}

.img_container {
  grid-area: img;
}
.info_container {
  grid-area: info;
  display: grid;
  grid-template-columns: 200px 160px;
  grid-template-rows: 37px;
}
.btn2 {
  cursor: pointer;
  margin-top: 14px;
  margin-left: 25px;
  color: white;
  font-size: 16px;
  font-family: "Montserrat", sans-serif;
  width: 181px;
  height: 36px;
  border-radius: 4px;
  border-style: hidden;
  background-color: v-bind(btn_color);
}
.btn2:hover {
  cursor: pointer;
  margin-top: 14px;
  margin-left: 25px;
  color: white;
  font-size: 16px;
  font-family: "Montserrat", sans-serif;
  width: 181px;
  height: 36px;
  border-radius: 4px;
  border-style: hidden;
  background-color: v-bind(btn_color_hover);
}
.btn:hover {
  color: white;
  font-size: 16px;
  font-family: "Montserrat", sans-serif;
  width: 181px;
  height: 36px;
  border-radius: 4px;
  border-style: hidden;
  background-color: #7899ff;
  transition: 0.3s;
}
.head {
  margin-left: 114px;
  margin-top: 40px;
  margin-bottom: 10px;
}
</style>
