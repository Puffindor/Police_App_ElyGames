<template>
  <div class="item">
    <span>{{ name }}</span>
    <span class="action">{{ action }}</span>
  </div>
</template>

<script>
export default {
  props: ["name", "action"],
  computed: {
    Color() {
      if (this.action.includes("+")) {
        return "#00BC7E";
      } else {
        return "#FF3939";
      }
    },
  },
};
</script>

<style>
.action {
  color: v-bind(Color);
}

.item {
  font-family: Arial;
  font-size: 18px;
  font-weight: 700;
  height: 80px;
  align-items: center;
  border-bottom: 1px solid #c6cddf;
  display: grid;
  grid-template-columns: 195px 135px;
}
</style>
