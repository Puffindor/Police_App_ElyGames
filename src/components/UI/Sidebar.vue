<template>
  <div class="sidebar">
    <div @click="SwitchTab(1)" class="nav_element">
      <Icone_home :size="IconsSize" :color="color" />
      <span :style="'color: ' + color[0]">Home</span>
    </div>
    <div @click="SwitchTab(2)" class="nav_element">
      <Icone_files :size="IconsSize" :color="color" />

      <span :style="'color: ' + color[1]">Criminal files</span>
    </div>

    <div @click="SwitchTab(3)" class="nav_element">
      <Icon_stuff :size="IconsSize" :color="color" />

      <span :style="'color: ' + color[2]">Inventory</span>
    </div>
    <div @click="SwitchTab(6)" class="nav_element">
      <Icon_car :size="IconsSize" :color="color" />

      <span :style="'color: ' + color[5]">Flotte</span>
    </div>
    <div @click="SwitchTab(4)" class="nav_element">
      <Icon_list :size="IconsSize" :color="color" />

      <span :style="'color: ' + color[3]">Call List</span>
    </div>
    <div @click="SwitchTab(5)" class="nav_element">
      <Icon_agents :size="IconsSize" :color="color" />
      <span :style="'color: ' + color[4]">Online Agents</span>
    </div>
    <div class="logout" @click="SwitchTab(11)">
      <Icon_logout :size="IconsSize" :color="color" />
      <span>Logout</span>
    </div>
  </div>
</template>

<script>
import Icon_agents from "@/Assets/icons/Icon_agents.vue";
import Icon_stuff from "@/Assets/icons/Icon_stuff.vue";
import Icon_car from "@/Assets/icons/Icon_car.vue";
import Icone_home from "@/Assets/icons/Icone_home.vue";
import Icone_files from "@/Assets/icons/Icone_files.vue";
import Icon_list from "@/Assets/icons/Icon_list.vue";
import Icon_logout from "../../Assets/icons/Icon_logout.vue";

export default {
  emits: ["cl"],
  components: {
    Icon_agents,
    Icon_stuff,
    Icon_car,
    Icone_home,
    Icone_files,
    Icon_list,
    Icon_logout,
  },
  props: {
    currentPageID: {
      default: 1,
    },
  },
  data() {
    return {
      iconsSize: "",
      pageID: {
        home: 1,
        files: 2,
        stuff: 3,
        list: 4,
        agents: 5,
        cars: 6,
      },
      color: ["#396aff", "#b4bdcd", "#b4bdcd", "#b4bdcd", "#b4bdcd", "#b4bdcd"], // [Home, Files, Stuff, cars,List, Agents]
    };
  },
  methods: {
    SwitchTab(id) {
      this.color[this.currentPageID - 1] = "#b4bdcd";
      this.color[id - 1] = "#396aff";

      this.$emit("cl", id);
    },
  },
  computed: {
    IconsSize() {
      switch (window.screen.width) {
        case 2047:
          return 25;
        case 3839:
          return 30;
        default:
          return 23;
      }
    },
  },
};
</script>

<style scoped>
span {
  color: #848fa4;
  margin-left: 21px;
}
.sidebar {
  width: 300px;
  max-height: 100vh;
  background-color: white;
  font-family: "Montserrat";
  font-size: 16px;
  box-shadow: 10px 0px 50px rgba(0, 0, 0, 0.08);
  z-index: 10;
}
.nav_element {
  margin-top: 49px;
  display: flex;
  align-items: center;
  margin-left: 42px;
  cursor: pointer;
}

.logout {
  margin-left: 42px;
  margin-top: 450px;
}

@media screen and (min-width: 2047px) {
  .sidebar {
    font-size: 18px;
  }
  .logout {
    margin-top: 450px;
  }
}
@media screen and (min-width: 2559px) {
  .sidebar {
    font-size: 18px;
  }
  .logout {
    margin-top: 830px;
  }
}
@media screen and (min-width: 3839px) {
  .sidebar {
    font-size: 22px;
    width: 400px;
  }
  .logout {
    margin-top: 1350px;
  }
  .nav_element {
    margin-top: 60px;
  }
}
/* 2048×1080 2K */
/* 2560x1440 3K */
/* 3840 Х 2160 */
</style>
