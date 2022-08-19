<template>
  <div>
    <h1>Flotte Management</h1>
    <div class="flex">
      <div class="btn_container">
        <button class="btn">Prendre la voiture</button>
        <span class="bold">Mettre la machine en service</span>
        <span class="light">La voiture apparaîtra dans le garage du LSPD.</span>
      </div>
      <div class="other">
        <div class="total cars">
          <span class="total len">{{ this.Search.length }}</span>
          <span class="total string">Car</span>
        </div>
        <div class="fuel">
          <div class="len"><span>1500L</span></div>
          <span class="string">Essence en stock</span>
        </div>
      </div>

      <div class="search_inp">
        <input placeholder="Search" v-model="SearchInput" />

        <Icon_search_small />
      </div>
    </div>

    <div class="list_head">
      <span>Vehicule</span>
      <span>Name</span>
      <span>Rank</span>
      <span>Etat</span>
      <span>Fuel</span>
    </div>
    <div class="list_container">
      <div v-for="car in Search" class="item">
        <span>{{ car.vehicule }}</span>
        <span>{{ car.name }}</span>
        <span>{{ car.rank }}</span>
        <span>{{ car.health }}</span>
        <span>{{ car.fuel }}</span>
        <button class="btn_location"><Icon_location /></button>
      </div>
    </div>
  </div>
</template>

<script>
import Icon_search_small from "@/icons/Icon_search_small.vue";
import Icon_location from "@/icons/Icon_location.vue";
export default {
  components: { Icon_search_small, Icon_location },

  props: ["cars"],
  data() {
    return {
      List: [],
      SearchResault: [],
      SearchInput: "",
    };
  },
  methods: {},
  computed: {
    Search() {
      if (this.SearchInput) {
        return this.cars.filter((el) =>
          el.name
            .toLocaleLowerCase()
            .includes(this.SearchInput.toLocaleLowerCase())
        );
        // this.List = this.SearchResault;
      } else {
        return this.cars;
      }
    },
  },
};
</script>

<style scoped>
@import url("https://fonts.googleapis.com/css2?family=Montserrat:wght@700&display=swap");
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

.total_fuel {
  display: flex;
  justify-content: center;
  align-items: center;
  width: 136px;
  height: 134px;
}

.len {
  font-family: Arial;
  font-size: 32px;
  font-weight: 700;
}
.string {
  font-family: "Segoe UI";
  font-size: 18px;
  font-weight: 500;
  color: #65789a;
}

.fuel {
  height: 64px;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  margin-left: 40px;
}
.total {
  font-family: Arial;

  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
  width: 136px;
  height: 64px;
  border-right: 1px solid #e5e8ec;
}
.flex {
  margin-left: 114px;
  display: grid;
  grid-template-columns: 593px 351px;
  grid-template-rows: 55px 53px;
  row-gap: 26px;
  column-gap: 440px;
  margin-top: 26px;
  grid-template-areas: "button other " "search other";
}
.other {
  display: flex;
  align-items: center;
  width: 351px;
  height: 134px;
  border-radius: 10px;
  background-color: #f0f3f9;
  grid-area: other;
}
.btn_location {
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
.list_container {
  width: 1412px;
  display: flex;
  justify-content: flex-start;
  overflow: auto;
  max-height: 550px;
  margin-left: 114px;
  margin-top: 40px;
}
.item {
  display: grid;
  grid-template-columns: 268px 277px 446px 162px 181px 36px;
  border-bottom: 1px solid #c6cddf;
  font-family: Arial;
  font-size: 18px;
  font-weight: 700;
  height: 80px;
  align-items: center;
}
.list_head {
  font-family: "Segoe UI";
  font-size: 18px;
  font-weight: 600;
  color: #a1acc0;
  display: grid;
  grid-template-columns: 268px 277px 446px 162px 50px;
  margin-left: 114px;
  margin-top: 30px;
}
.search_inp {
  grid-area: search;
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding-left: 14px;
  padding-right: 14px;

  width: 380px;
  height: 53px;
  border-radius: 6px;
  background-color: #e0e4ee;
}
input {
  border-style: hidden;
  color: #253042;
  background-color: transparent;
  outline: none;
  font-size: 16px;
  font-family: "Segoe UI";
  font-weight: 600;
}
.light {
  font-family: "Segoe UI";
  font-size: 16px;
  color: #65789a;
  font-weight: 400;
  grid-area: light;
}
.bold {
  font-family: "Segoe UI";
  font-size: 18px;
  font-weight: 700;
  color: #202c3e;
  grid-area: bold;
}
.btn {
  width: 211px;
  height: 55px;
  border-radius: 4px;
  background-color: #396aff;

  font-family: "Montserrat", sans-serif;
  font-size: 16px;
  color: white;
  grid-area: button;
}
.btn_container {
  grid-area: button;
  height: 55px;
  width: 535px;
  display: grid;
  grid-template-columns: 211px 324px;
  grid-template-rows: 25px 25px;

  column-gap: 29px;
  grid-template-areas: "button bold" "button light";
}

h1 {
  margin-top: 60px;
  margin-left: 114px;
}
</style>
