<template>
  <span class="time">{{ call.time }}</span>
  <span class="name">{{ call.name }}</span>
  <span class="rank">{{ call.massage }}</span>
  <span class="distance">{{ call.distance }} </span>
  <button class="btn_accept">Accept</button>
  <button class="btn_loc"><Icon_location /></button>

  <button @click="Delete" class="btn_cross"><Icon_cross /></button>
</template>

<script>
import Icon_location from "../../../Assets/icons/Icon_location.vue";
import Icon_cross from "../../../Assets/icons/Icon_cross.vue";

export default {
  emits: ["deleteCall"],
  props: ["call"],
  components: { Icon_location, Icon_cross },
  methods: {
    Delete() {
      this.$emit("deleteCall", this.call.id);
    },
  },
};
</script>

<style scoped>
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

.btn_loc {
  margin-right: 10px;
  cursor: pointer;
  display: flex;
  justify-content: center;
  align-items: center;
  border-style: hidden;
  width: 36px;
  height: 36px;

  background-color: #00bc7e;
  border-radius: 8px;
}

.btn_cross {
  cursor: pointer;
  display: flex;
  justify-content: center;
  align-items: center;
  border-style: hidden;
  width: 36px;
  height: 36px;

  background-color: #e13c3c;
  border-radius: 8px;
}

.btn_accept {
  margin-right: 10px;
  cursor: pointer;
  font-family: "Montserrat", sans-serif;
  border-style: hidden;
  border-radius: 4px;
  width: 119px;
  height: 36px;
  background-color: #396aff;
  color: white;
  font-size: 16px;
}
</style>
