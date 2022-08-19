<template>
  <span>{{ Log() }}</span>
  <div class="container2">
    <button class="btn btn_right" @click="Backward"><Chevron_right /></button>
    <div class="medal_item" v-for="medal in Forward" :key="medal.id">
      <div>
        <img :src="medal.img" v-if="medal.img" />
      </div>
    </div>

    <button class="btn" @click="Forward1"><Chevron_right /></button>
  </div>
</template>

<script>
import Chevron_right from "@/icons/chevron_right.vue";
import Chevron_left from "@/icons/chevron_left.vue";
export default {
  props: ["Medals"],
  data() {
    return {
      first: 0,
      last: 8,
      List: [],
    };
  },
  methods: {
    Forward1() {
      if (this.last < this.Medals.length) {
        this.last = this.last + 8;
        this.first = this.first + 8;
        if (this.Medals.length < this.last) {
          for (let i = 0; i < this.last - this.Medals.length; i++) {
            this.Forward.push({ img: "" });
            console.log(this.Medals.length);
          }
        }
      }
    },
    Backward() {
      if (this.last > this.Medals.length) {
        this.last = this.last - 8;
        this.first = this.first - 8;
        if (this.Medals.length < this.last) {
          for (let i = 0; i < this.last - this.Medals.length; i++) {
            this.Forward.push({ img: "" });
            console.log(this.Medals.length);
          }
        }
      }
    },
    Log() {
      if (this.Medals.length < 8) {
        this.List = this.Medals;
        for (let i = 0; i < 8 - this.Medals.length; i++) {
          this.List.push({ img: "" });
        }
      } else {
        for (let i = 0; i < 8; i++) {
          this.List = this.Medals.slice(0, 8);
        }
      }
    },
  },
  computed: {
    Forward() {
      return this.Medals.slice(this.first, this.last);
    },
  },
  components: { Chevron_right, Chevron_left },
};
</script>

<style scoped>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
img {
  width: 129px;
  height: 129px;
}

.btn_right {
  transform: rotate(180deg);
}
.btn {
  width: 13px;
  height: 40px;
  display: flex;
  justify-content: center;
  align-items: center;
  background-color: transparent;
}
.container2 {
  display: flex;
  justify-content: space-between;
  align-items: center;
  overflow-x: auto;
  width: 1356px;

  margin-left: 18px;
  margin-bottom: 21px;
}
.medal_item {
  display: flex;
  justify-content: center;
  align-items: center;
  width: 139px;
  height: 139px;
  border-radius: 4px;
  background-color: #f5f7fb;
}
</style>
