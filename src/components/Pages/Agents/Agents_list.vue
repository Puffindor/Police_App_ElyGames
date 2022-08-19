<template>
  <div>
    <span>{{ Invited() }}</span>
    <div class="item">
      <span @click="profile">{{ name }}</span>
      <span>{{ rank }}</span>
      <div class="status_container">
        <span>{{ status }} {{ Color() }} </span>
      </div>
      <span>{{ distance }}</span>
      <button @click="Invite" class="btn">{{ this.invite }}</button>
    </div>
  </div>
</template>

<script>
export default {
  emits: ["AgentID", "invited"],
  props: ["invited", "id", "name", "rank", "status", "distance"],
  data() {
    return {
      color: "#F6B73E",
      width: "156px",
      invite: "Invite",
      btn_color: "#396aff",
      btn_color_hover: "#7899FF",
    };
  },

  methods: {
    profile() {
      this.$emit("AgentID", this.id);
    },
    Color() {
      switch (this.status) {
        case "AFK":
          this.color = "#F6B73E";
          this.width = "65px";
          break;
        case "On duty":
          this.color = "#396AFF";
          this.width = "97px";
          break;
        case "Do not disturb":
          this.color = "#E53F3F";
          this.width = "156px";
          break;
        case "Need a parthner":
          this.color = "#00BC7E";
          this.width = "156px";
          break;
      }
    },
    Invited() {
      if (this.invited === true) {
        this.invite = "Invite send";
        this.btn_color = "#E0E7EF";
        this.btn_color_hover = "#E0E7EF";
      }
    },
    Invite() {
      this.$emit("invited", this.id);
    },
  },
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
.btn {
  color: white;
  font-size: 16px;
  font-family: "Montserrat", sans-serif;
  width: 107px;
  height: 36px;
  border-radius: 4px;
  border-style: hidden;
  background-color: v-bind(btn_color);
}
.btn:hover {
  color: white;
  font-size: 16px;
  font-family: "Montserrat", sans-serif;
  width: 107px;
  height: 36px;
  border-radius: 4px;
  border-style: hidden;
  background-color: v-bind(btn_color_hover);
  transition: 0.3s;
}

.status_container {
  /* min-width: 65px;
  max-width: 165px; */
  width: v-bind(width);
  background-color: v-bind(color);
  height: 36px;
  border-radius: 6px;
  display: flex;
  align-items: center;
  justify-content: center;
  /* background-color: #396aff; */
  color: white;
}
.item {
  width: 1400px;
  height: 80px;
  border-bottom: solid 1px #c6cddf;
  align-items: center;
  font-family: Arial;
  font-size: 18px;
  font-weight: 600;
  display: grid;
  grid-template-columns: 241px 197px 636px 206px 140px;
  margin-right: 20px;
}
@media screen and (max-width: 1401px) {
  .item {
    grid-template-columns: 241px 240px 324px 144px 140px;
    width: 1080px;
  }
}
</style>
