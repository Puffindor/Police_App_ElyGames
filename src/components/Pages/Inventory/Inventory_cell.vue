<template>
  <div class="amount" v-if="item.amount">
    <span>{{ item.amount }}</span>
  </div>
  <img :src="Img" />
</template>

<script>
export default {
  props: ["item"],
  data() {
    return {
      img: "",
    };
  },
  computed: {
    Img() {
      return (this.img = this.item.img);
    },
  },
};
</script>

<style scoped>
.amount {
  display: flex;
  align-items: center;
  justify-content: center;
  font-family: Arial;
  font-size: 18px;
  font-weight: 700;
  color: #3c6cff;
  margin-top: 10px;
  margin-left: 90px;
  width: 35px;
  height: 23px;
  border-radius: 4px;
  background-color: #d3defd;
}
</style>
