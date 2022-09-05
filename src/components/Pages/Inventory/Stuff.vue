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

      if (this.inventory.length < this.ScreenSize) {
        for (let i = 0; i < this.ScreenSize - this.inventory.length; i++) {
          this.List.push({ img: "", amount: "" });
        }
      }
    },

    Add() {
      this.List[this.List.findIndex((el) => el.amount === "")].amount = 100;
      this.List[
        this.List.findIndex((el) => el.img === "")
      ].img = require("../../../Assets/Stick.png");
      if (this.List.findIndex((el) => el.amount === "") === -1) {
        for (let i = 0; i < this.ScreenSize2; i++) {
          this.List.push({ amount: "", img: "" });
        }
      }
    },
  },
  computed: {
    ScreenSize() {
      switch (window.screen.width) {
        case 1400:
          return 20;
        case 2560:
          return 56;
        case 3840:
          return 165;
        default:
          return 30;
      }
    },
    ScreenSize2() {
      switch (window.screen.width) {
        case 1400:
          return 4;
        case 2560:
          return 8;
        case 3840:
          return 15;
        default:
          return 6;
      }
    },
  },
  components: { Inventory_cell, Inventory_history },
};
</script>

<style scoped>
@import "./Stuff.css";
</style>
