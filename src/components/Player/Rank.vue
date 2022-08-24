<template>
  <div class="wrapper1">
    <h1>Rank progress</h1>
    <div class="next">
      <div>{{ Rank }}</div>
      <div>{{ NextRank }}</div>
    </div>
    <div class="straps">
      <component
        :is="this.possibleRanks[this.possibleRanks.length - 1].strap"
        :size="this.Size"
        v-if="this.exp <= this.ranks[this.ranks.length - 1].exp"
      ></component>
      <component
        :is="this.test[0].strap"
        :size="this.Size"
        v-if="this.exp <= this.ranks[this.ranks.length - 1].exp"
      ></component>
    </div>

    <div class="progress_bar">
      <div class="progress_bar_inner"></div>
    </div>
    <div v-if="this.exp < this.ranks[this.ranks.length - 1].exp">
      {{ XPtoNext }} ex to {{ NextRank }}
    </div>
  </div>
</template>

<script>
import Lieutenant_1 from "@/Assets/straps/Lieutenant_1.vue";
import Lieutenant_2 from "@/Assets/straps/Lieutenant_2.vue";
export default {
  emits: ["rank"],
  components: { Lieutenant_1, Lieutenant_2 },
  props: ["exp", "ranks", "agent"],
  data() {
    return {
      NextRanks: [],
      possibleRanks: [],
      svgSize: 24,
    };
  },

  computed: {
    Size() {
      switch (window.screen.width) {
        case 2560:
          return 32;
        case 3840:
          return 40;
        default:
          return 24;
      }
    },

    NextRank() {
      this.NextRanks = this.ranks.filter((el) => el.exp > this.exp);
      if (this.NextRanks.length > 0) {
        return this.NextRanks[0].name;
      } else {
        return "Max Rank";
      }
    },
    test() {
      if (this.exp <= this.ranks[this.ranks.length - 1].exp) {
        return this.ranks.filter((el) => el.exp > this.exp);
      }
    },
    Rank() {
      this.possibleRanks = this.ranks.filter((el) => el.exp <= this.exp);

      return this.possibleRanks[this.possibleRanks.length - 1].name;
    },
    Progress() {
      if (this.exp <= this.ranks[this.ranks.length - 1].exp) {
        return `${
          100 -
          (this.XPtoNext /
            (this.NextRanks[0].exp -
              this.possibleRanks[this.possibleRanks.length - 1].exp)) *
            100
        }%`;
      }
    },
    XPtoNext() {
      if (this.NextRanks.length > 0) {
        if (this.agent === true) {
          this.$emit(
            "agent_rank",
            this.possibleRanks[this.possibleRanks.length - 1].name
          );
          console.log(this.possibleRanks[this.possibleRanks.length - 1].name);
        } else {
          console.log(this.possibleRanks[this.possibleRanks.length - 1].name);
          this.$emit(
            "rank",
            this.possibleRanks[this.possibleRanks.length - 1].name
          );
        }

        return this.NextRanks[0].exp - this.exp;
      }
    },
  },
};
</script>

<style scoped>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

img {
  width: 100px;
  height: 50px;
}

.straps {
  display: flex;
  justify-content: space-between;
  padding-left: 53px;
  padding-right: 53px;
  width: 100%;
  margin-bottom: 22px;
}
.next {
  padding-left: 20px;
  padding-right: 20px;
  width: 100%;
  display: flex;
  justify-content: space-between;
  font-family: "Segoe UI";
  font-size: 18px;
  font-weight: 700;
}
.wrapper1 {
  font-family: "Segoe UI";
  font-size: 18px;
  font-weight: 700;
  display: flex;
  justify-content: flex-start;
  justify-items: center;
  width: 100%;
  height: 100%;
  display: flex;
  flex-wrap: wrap;
  flex-direction: column;
  align-content: space-around;
  align-items: center;
}

.progress_bar_inner {
  width: v-bind(Progress);
  height: 10px;
  background-color: #396aff;
  border-radius: 8px;
  transition: 0.5s;
}

.progress_bar {
  justify-content: flex-start;
  align-items: center;
  display: flex;
  width: 82%;
  height: 10px;
  border-radius: 8px;
  border: 1px solid #707070;
  margin-bottom: 18px;
}
@media screen and (min-width: 2559px) {
  .wrapper1 {
    justify-content: center;
  }
}

@media screen and (min-width: 3839px) {
  .progress_bar_inner {
    height: 20px;
  }

  .progress_bar {
    height: 20px;
  }
  .wrapper1 {
    font-size: 25px;
  }
  .next {
    font-size: 25px;
  }
  .straps {
    padding-left: 70px;
    padding-right: 70px;
  }
}
</style>
