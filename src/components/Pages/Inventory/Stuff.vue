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
        ].img = require("@//Assets/Stick.png");
        if (this.List.findIndex((el) => el.amount === "") === -1) {
          for (let i = 0; i < 4; i++) {
            this.List.push({ amount: "", img: "" });
          }
        }
      } else {
        this.List[this.List.findIndex((el) => el.amount === "")].amount = 100;
        this.List[
          this.List.findIndex((el) => el.img === "")
        ].img = require("@//Assets/Stick.png");
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
@import "./Stuff.css";
</style>
