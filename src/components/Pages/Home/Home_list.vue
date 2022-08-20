<template>
  <span class="time">{{ time }}</span>
  <span class="code">{{ code }}</span>
  <span class="name">{{ name }}</span>
  <span class="rank">{{ rank }}</span>
  <span class="distance">{{ distance }} </span>
  <button class="btn_accept">Accept</button>

  <button class="btn_loc"><Icon_location /></button>
  <button @click="Delete" class="btn_cross"><Icon_cross /></button>
</template>

<script>
import Icon_cross from "@/Assets/icons/Icon_cross.vue";
import Icon_location from "@/Assets/icons/Icon_location.vue";

export default {
  emits: ["delete"],
  props: ["id", "name", "time", "code", "rank", "distance"],
  components: { Icon_cross, Icon_location },
  methods: {
    Delete() {
      this.$emit("delete", this.id);
    },
  },
};
</script>

<style>
@import "./Home_list.css";
</style>
