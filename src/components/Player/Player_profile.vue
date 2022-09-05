<template>
  <div>
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
          <div v-for="crime in this.PlayerProfile.history" class="list_item1">
            <Agent_profile_list :name="crime.name" :status="crime.status" />
          </div>
        </div>
      </div>
      <div class="rank_container">
        <Rank
          :exp="this.PlayerProfile.exp"
          :ranks="this.ranks"
          @rank="rank"
          :agent="false"
        />
      </div>
      <div class="medals">
        <div class="medals_head">Medals</div>
        <Medals_list :Medals="this.PlayerProfile.medals" />
      </div>
      <div class="left_column">
        <div class="img_container">
          <img class="img" :src="img" />

          <button @click="Show" class="btn2">Edit profile</button>
        </div>
        <div class="name_container">
          <span class="name">{{ this.PlayerProfile.name }}</span>
          <span class="status_container">
            {{ this.PlayerProfile.status }}
          </span>
          <span class="rank">{{ this.PlayerProfile.rank }}</span>
        </div>
        <div class="info_container">
          <span class="b"
            ><span class="h">Birthday: </span
            >{{ this.PlayerProfile.birthday }}</span
          >
          <span class="b"
            ><span class="h">Id: </span>{{ this.PlayerProfile.id }}</span
          >
          <span class="b"
            ><span class="h">Phone: </span>{{ this.PlayerProfile.phone }}</span
          >
        </div>
      </div>
    </div>
    <Player_profile_modal
      v-if="ShowModal"
      :PlayerProfile="PlayerProfile"
      @close="Show"
      @upload_player="Upload"
    />
  </div>
</template>

<script>
import Player_profile_modal from "./Player_profile_modal.vue";
import Medals_list from "./Medals_list.vue";
import Agent_profile_list from "../Pages/Agents/Agent_profile_list.vue";
import Rank from "./Rank.vue";

export default {
  emits: ["upload_player"],
  props: ["PlayerProfile", "ranks"],
  data() {
    return {
      color: "#396aff",
      btn_color: "#396aff",
      btn_color_hover: "#7899FF",
      invite: "Invite",
      avatar: "",
      base_avatar: "../../icons/base_avatar.png",
      ShowModal: false,
    };
  },
  methods: {
    rank(rank) {
      this.$emit("rank", rank);
    },
    Upload(link) {
      this.$emit("upload_player", link);
    },
    Show() {
      this.ShowModal = !this.ShowModal;
    },
    Color() {
      switch (this.PlayerProfile.status) {
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
      if (this.PlayerProfile.avatar) {
        return (this.avatar = this.PlayerProfile.avatar);
      } else {
        return (this.avatar = require("../../Assets/icons/base_avatar.png"));
      }
    },
  },

  components: { Player_profile_modal, Medals_list, Agent_profile_list, Rank },
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

.medals_head {
  font-family: Arial, Helvetica, sans-serif;
  font-size: 28px;
  font-weight: 700;
  margin-top: 25px;
  margin-bottom: 22px;
}
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

.list_container1 {
  width: 570px;
  max-height: 400px;
  overflow: auto;
  display: flex;
  justify-content: flex-start;
  flex-wrap: wrap;
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
  display: flex;
  justify-content: center;
  flex-wrap: wrap;
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

@media screen and (max-width: 1401px) {
  .case_history {
    width: 409px;
  }
  .list_container1 {
    width: 409px;
  }
  .list_item1 {
    width: 350px;
    grid-template-columns: 200px 149px;
  }
  .list_head {
    grid-template-columns: 200px 149px;
  }
  h2 {
    margin-left: 103px;
  }
  .left_column {
    width: 592px;
  }
  .name_container {
    width: 340px;
  }
  .rank_container {
    width: 592px;
  }
  .medals {
    width: 1020px;
  }
  .profile {
    grid-template-columns: 592px 449px;
    margin-left: 40px;
  }
  .head {
    margin-left: 40px;
  }
}
@media screen and (min-width: 2047px) {
}
@media screen and (min-width: 2559px) {
  .medals {
    width: 100%;
  }
  .profile {
    grid-template-columns: 56.5vw 585px;
    grid-template-rows: 31.5vh 31.5vh 15vh;
    margin-top: 45px;
  }
  .head {
    margin-top: 50px;
  }
  .img {
    width: 360px;
    height: 360px;
  }
  .btn2 {
    width: 360px;
  }

  .left_column {
    width: 100%;
    height: 100%;
    grid-template-columns: 380px 1fr;
  }
  .name_container {
    width: 95%;
    align-self: flex-start;
  }
  .info_container {
    grid-template-columns: 1fr;
    grid-template-rows: repeat(3, 1fr);
  }
  .rank_container {
    width: 100%;
    height: 100%;
  }
  .case_history {
    height: 100%;
  }
  .list_container1 {
    max-height: 82%;
  }
}

@media screen and (min-width: 3839px) {
  .profile {
    grid-template-columns: 56.5vw 25vw;
    grid-template-rows: 31.5vh 31.5vh 18vh;
  }
  .medals {
    width: 100%;
  }

  .head {
    margin-top: 50px;
  }
  .img {
    width: 100%;
    height: 85%;
  }
  .btn2 {
    width: 100%;
  }
  .btn2:hover {
    cursor: pointer;
    margin-top: 14px;
    margin-left: 25px;
    color: white;
    font-size: 16px;
    font-family: "Montserrat", sans-serif;
    width: 100%;
    height: 36px;
    border-radius: 4px;
    border-style: hidden;
    background-color: v-bind(btn_color_hover);
  }
  .name {
    font-size: 40px;
  }
  .rank {
    font-size: 30px;
  }
  .left_column {
    width: 100%;
    height: 100%;
    grid-template-columns: 587px 1fr;
    column-gap: 50px;
  }
  .name_container {
    width: 95%;
    grid-template-columns: 500px 1fr;
    align-self: center;
    align-self: flex-start;
    grid-template-rows: 80px 80px;
  }
  .info_container {
    grid-template-columns: 1fr;
    grid-template-rows: repeat(3, 1fr);
  }
  .b {
    font-size: 30px;
  }
  .h {
    font-size: 30px;
  }
  .rank_container {
    width: 100%;
    height: 100%;
  }
  .case_history {
    height: 100%;
    width: 100%;
  }
  .list_container1 {
    max-height: 85%;
    width: 95%;
  }
  h2 {
    margin-left: 350px;
  }
  .list_item1 {
    width: 90%;
    grid-template-columns: repeat(2, 50%);
    padding-left: 30px;
    padding-right: 30px;
    font-size: 20px;
  }
  .list_head {
    width: 100%;
    grid-template-columns: 68% 20%;
    margin-left: 80px;
    font-size: 20px;
  }
  .status_container {
    font-size: 23px;
  }
}

/* 2048×1080 2K */
/* 2560x1440 3K */
/* 3840 Х 2160 */
</style>
