<template>
  <!-- <button @click="Add">add</button> -->
  <div class="Stuff">
    <div class="cont">
      <span>{{ Log() }}</span>
      <h1>Inventory</h1>
      <div class="inventory">
        <div @click="Log" class="cell" v-for="item in this.List">
          <Inventory_cell :item="item" />
        </div>
      </div>
    </div>
    <div>
      <h2>History of inventory</h2>
      <div class="list_head">
        <span>Name</span>
        <span>Action</span>
      </div>
      <div class="container">
        <div v-for="event in InventoryHistory">
          <Inventory_history :name="event.name" :action="event.action" />
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import Inventory_cell from "./Inventory_cell.vue";
import Inventory_history from "./Inventory_history.vue";
export default {
  props: ["inventory", "InventoryHistory"],
  data() {
    return {
      List: [{}],
    };
  },
  methods: {
    Log() {
      this.List = this.inventory;
      if (window.screen.width < 1401) {
        if (this.inventory.length < 20) {
          for (let i = 0; i < 20 - this.inventory.length; i++) {
            this.List.push({ img: "", amount: "" });
          }
        }
      } else {
        if (this.inventory.length < 30) {
          for (let i = 0; i < 30 - this.inventory.length; i++) {
            this.List.push({ img: "", amount: "" });
          }
        }
      }
    },
    Add() {
      if (window.screen.width < 1401) {
        this.List[this.List.findIndex((el) => el.amount === "")].amount = 100;
        this.List[
          this.List.findIndex((el) => el.img === "")
        ].img = require("@/components/Assets/Stick.png");
        if (this.List.findIndex((el) => el.amount === "") === -1) {
          for (let i = 0; i < 4; i++) {
            this.List.push({ amount: "", img: "" });
          }
        }
      } else {
        this.List[this.List.findIndex((el) => el.amount === "")].amount = 100;
        this.List[
          this.List.findIndex((el) => el.img === "")
        ].img = require("@/components/Assets/Stick.png");
        if (this.List.findIndex((el) => el.amount === "") === -1) {
          for (let i = 0; i < 6; i++) {
            this.List.push({ amount: "", img: "" });
          }
        }
      }
    },
  },
  computed: {},
  components: { Inventory_cell, Inventory_history },
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
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
h1 {
  margin-top: 60px;
  margin-left: 114px;
}

.container {
  display: flex;
  flex-wrap: wrap;
  max-height: 720px;
  overflow: auto;
  width: 360px;
}
.list_head {
  font-family: "Segoe UI";
  font-size: 18px;
  font-weight: 600;
  color: #a1acc0;

  display: grid;
  grid-template-columns: 195px 53px;
  margin-top: 30px;
}
.cell {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
  width: 138px;
  height: 138px;
  border-radius: 6px;
  background-color: #f0f3f9;
}

h2 {
  font-family: Arial;
  font-size: 32px;
  font-weight: 800;
  margin-top: 60px;
}
.Stuff {
  display: grid;
  grid-template-columns: 1020px 700px;
  column-gap: 35px;
}
.inventory {
  width: 920px;
  height: 750px;
  overflow: auto;
  display: grid;
  grid-template-columns: repeat(6, 138px);
  column-gap: 14px;
  row-gap: 14px;

  margin-left: 114px;
  margin-top: 30px;
}

@media screen and (max-width: 1401px) {
  .inventory {
    width: 610px;
    margin-left: 40px;
    grid-template-columns: repeat(4, 138px);
  }
  h1 {
    margin-left: 40px;
  }
  .Stuff {
    grid-template-columns: 650px 400px;
  }
}
</style>
