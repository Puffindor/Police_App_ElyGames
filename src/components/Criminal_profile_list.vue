<template>
  <span>{{ date }}</span>
  <span>{{ code }}</span>
  <span>{{ stations }}</span>
  <span>{{ motive }}</span>
  <span class="term">{{ term }}</span>
</template>

<script>
export default {
  props: ["date", "code", "stations", "motive", "term"],
  computed: {
    Color() {
      switch (this.term) {
        case "EN JUGEMENT":
          return "#464646";
        case "Innocent":
          return "#00BC7E";
        default:
          return "#E13C3C";
      }
    },
  },
};
</script>

<style scoped>
.term {
  color: v-bind(Color);
  justify-self: center;
}
</style>
