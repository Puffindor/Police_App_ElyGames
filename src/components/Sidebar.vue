<template>
  <div @click="SwitchTab(1)" class="nav_element">
    <Icone_home :color="color" />
    <span :style="'color: ' + color[0]">Home</span>
  </div>
  <div @click="SwitchTab(2)" class="nav_element">
    <Icone_files :color="color" />

    <span :style="'color: ' + color[1]">Files</span>
  </div>

  <div @click="SwitchTab(3)" class="nav_element">
    <Icon_stuff :color="color" />

    <span :style="'color: ' + color[2]">Stuff</span>
  </div>
  <div @click="SwitchTab(4)" class="nav_element">
    <Icon_list :color="color" />

    <span :style="'color: ' + color[3]">List</span>
  </div>
  <div @click="SwitchTab(5)" class="nav_element">
    <Icon_agents :color="color" />
    <span :style="'color: ' + color[4]">Agents</span>
  </div>
  <div style="margin-top: 526px" class="nav_element">
    <Icon_logout :color="color" />
    <span>Logout</span>
  </div>
</template>

<script>
import Icone_home from "@/icons/Icone_home.vue";
import Icone_files from "@/icons/Icone_files.vue";
import Icon_stuff from "@/icons/Icon_stuff.vue";
import Icon_list from "@/icons/Icon_list.vue";
import Icon_agents from "@/icons/Icon_agents.vue";
import Icon_logout from "../icons/Icon_logout.vue";
export default {
  components: {
    Icone_home,
    Icone_files,
    Icon_stuff,
    Icon_list,
    Icon_agents,
    Icon_logout,
  },
  props: {
    currentPageID: {
      default: 1,
    },
  },
  data() {
    return {
      pageID: {
        home: 1,
        files: 2,
        stuff: 3,
        list: 4,
        agents: 5,
      },
      color: ["#396aff", "#b4bdcd", "#b4bdcd", "#b4bdcd", "#b4bdcd"], // [Home, Files, Stuff, List, Agents]
    };
  },
  methods: {
    SwitchTab(id) {
      this.color[this.currentPageID - 1] = "#b4bdcd";
      this.color[id - 1] = "#396aff";

      this.$emit("cl", id);
    },
  },
};
</script>

<style scoped>
.side_bar {
  width: 300px;
  height: 1080px;
  background-color: white;
  font-family: "Montserrat";

  font-size: 16px;
  box-shadow: 10px 0px 50px rgba(0, 0, 0, 0.08);

  z-index: 1;
}
span {
  color: #848fa4;
  margin-left: 21px;
}
.nav_element {
  margin-top: 49px;
  display: flex;
  align-items: center;
  margin-left: 42px;
  cursor: pointer;
}
</style>
