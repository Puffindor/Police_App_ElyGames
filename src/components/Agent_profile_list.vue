<template>
  <span class="name1">{{ name }}</span>
  <div class="list_status_container">
    <span>{{ status }}</span>
    <spna>{{ Color() }}</spna>
  </div>
</template>

<script>
export default {
  props: ["name", "status"],
  data() {
    return {
      color: "#DDE5FD",
      text_color: "#FF3939",
      width: "20px",
    };
  },
  methods: {
    Color() {
      console.log(this.status);
      switch (this.status) {
        case "Complited":
          this.color = "#DDE5FD";
          this.text_color = "#396AFF";
          this.width = "122px";
          break;
        case "In  progress":
          this.color = "#D9FFF3";
          this.text_color = "#00BC7E";
          this.width = "127px";
          break;
        case "Abandonned":
          this.color = "#FFE4E4";
          this.text_color = "#FF3939";
          this.width = "139px";
          break;
      }
    },
  },
};
</script>

<style scoped>
.name1 {
  justify-self: flex-start;
}
.list_status_container {
  display: flex;
  justify-content: center;
  align-items: center;
  width: v-bind(width);
  height: 36px;
  border-radius: 4px;
  background-color: v-bind(color);
  color: v-bind(text_color);
}
</style>
