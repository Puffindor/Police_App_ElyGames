<template>
  <span>{{ (Size(), Log()) }}</span>
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
import Chevron_left from "../../Assets/icons/chevron_left.vue";
import Chevron_right from "../../Assets/icons/chevron_right.vue";
export default {
  props: ["Medals"],
  data() {
    return {
      first: 0,
      last: 8,
      emptyCels: 10,
      List: [],
      scroll: 8,
      count: 0,
      adapt: false,
    };
  },
  methods: {
    Forward1() {
      if (this.last < this.Medals.length) {
        this.count += 1;
        this.last = this.last + this.scroll;
        this.first = this.first + this.scroll;
        if (this.Medals.length < this.last) {
          for (let i = 0; i < this.last - this.Medals.length; i++) {
            this.Forward.push({ img: "" });
          }
        }
      }
    },
    Backward() {
      if (this.count > 0) {
        this.count -= 1;
        this.last = this.last - this.scroll;
        this.first = this.first - this.scroll;
        if (this.Medals.length < this.last) {
          for (let i = 0; i < this.last - this.Medals.length; i++) {
            this.Forward.push({ img: "" });
          }
        }
      }
    },
    Log() {
      if (this.Medals.length < this.emptyCels) {
        this.List = this.Medals;
        for (let i = 0; i < this.emptyCels - this.Medals.length; i++) {
          this.List.push({ id: Math.random(), img: "" });
        }
      } else {
        for (let i = 0; i < 8; i++) {
          this.List = this.Medals.slice(0, this.emptyCels);
        }
      }
    },

    Size() {
      if (this.adapt === false) {
        switch (window.screen.width) {
          case 1400:
            this.last = 6;
            this.adapt = true;
            break;
          case 2560:
            this.last = 12;
            this.adapt = true;
            this.emptyCels = 12;
            break;
          case 3840:
            this.last = 17;
            this.adapt = true;
            this.emptyCels = 17;
            console.log(window.screen.width);
            break;
          default:
            this.last = 8;
            this.adapt = true;
            break;
        }
      }
    },
  },
  computed: {
    Forward() {
      return this.Medals.slice(this.first, this.last);
    },
  },
  components: { Chevron_left, Chevron_right },
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
  /* width: 1356px; */
  width: 98%;

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
@media screen and (max-width: 1401px) {
  .container2 {
    width: 980px;
  }
  @media screen and (min-width: 2559px) {
  }
}
</style>
