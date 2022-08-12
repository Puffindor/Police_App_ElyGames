<template>
  <h1>Police Profile</h1>
  <span>{{ Color() }}</span>
  <div class="profile">
    <div class="left_column">
      <div class="img_container">
        <div class="img"></div>
        <button class="btn">Invite</button>
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
</template>

<script>
export default {
  props: ["agent_profile"],
  data() {
    return {
      color: "#396aff",
    };
  },
  methods: {
    Color() {
      console.log(this.agent_profile.status);
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
};
</script>

<style scoped>
@import url("https://fonts.googleapis.com/css2?family=Montserrat:wght@700&display=swap");
.img {
  width: 181px;
  height: 181px;
  margin-top: 25px;
  margin-left: 25px;
  background-color: aqua;
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

.left_column {
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
.btn {
  margin-top: 14px;
  margin-left: 25px;
  color: white;
  font-size: 16px;
  font-family: "Montserrat", sans-serif;
  width: 181px;
  height: 36px;
  border-radius: 4px;
  border-style: hidden;
  background-color: #396aff;
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
.profile {
  margin-top: 10px;
  margin-left: 40px;
}
h1 {
  margin-left: 40px;
  margin-top: 60px;
}
</style>
