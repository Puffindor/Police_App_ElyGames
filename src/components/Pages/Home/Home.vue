<template>
  <div class="Home">
    <div class="codes">
      <div>
        <div class="code_container">
          <span>Code - 1</span>
        </div>
      </div>
      <div>
        <div class="code_container">
          <span>Code - 2</span>
        </div>
      </div>
      <div>
        <div class="code_container">
          <span>Code - 3</span>
        </div>
      </div>
      <div>
        <div class="code_container">
          <span>Code - 4</span>
        </div>
      </div>
      <div>
        <div
          style="background-color: #ffe1e1; color: #ff3939"
          class="code_container"
        >
          <span>Code - 5</span>
        </div>
      </div>
    </div>
    <div>
      <div class="descriptions">
        <div class="descrription">
          <span>
            * Immediate support is required. This code will be sent to all
            departments without exception
          </span>
        </div>
        <div class="descrription">
          <span> * Support needed. Will be sent only to your department </span>
        </div>
        <div class="descrription">
          <span>
            * Calling a crew without sirens. Will be sent only to your
            department</span
          >
        </div>
        <div class="descrription">
          <span>
            * Calling a crew with sirens. Will be sent only to your
            department</span
          >
        </div>
        <div class="descrription">
          <span>
            * End call. Available only if you are near the location from which
            the call was made.</span
          >
        </div>
      </div>
    </div>
    <div class="list_contaiber"></div>
    <h1 class="header1">Call List</h1>
    <div class="list1">
      <div>Time<Icon_triangle class="triangle" /></div>
      <div>Code<Icon_triangle class="triangle" /></div>
      <div>Name<Icon_triangle class="triangle" /></div>
      <div>Rank<Icon_triangle class="triangle" /></div>
      <div>Distance<Icon_triangle class="triangle" /></div>
    </div>
    <div class="list_container1">
      <div class="listItem" v-for="(call, index) in callList">
        <Home_list
          @delete="Delete"
          :id="call.id"
          :time="call.time"
          :code="call.code"
          :name="call.name"
          :rank="call.rank"
          :distance="call.distance"
        />
      </div>
    </div>
  </div>
</template>

<script>
import Home_list from "./Home_list.vue";
import Icon_red_cross from "@/Assets/icons/Icon_red_cross.vue";
import Icon_triangle from "@/Assets/icons/Icon_triangle.vue";
import Icon_cross from "@/Assets/icons/Icon_cross.vue";
import Icon_location from "@/Assets/icons/Icon_location.vue";
export default {
  components: {
    Icon_location,
    Icon_cross,
    Icon_triangle,
    Home_list,
    Icon_red_cross,
  },

  data() {
    return {
      callList: [
        {
          id: Math.random(),
          time: "10:23",
          code: 1,
          name: "James Washington",
          rank: "Capitan 3",
          distance: "23.11 km",
        },
        {
          id: Math.random(),
          time: "10:23",
          code: 1,
          name: "James Washington",
          rank: "Capitan 3",
          distance: "23.11 km",
        },
        {
          id: Math.random(),
          time: "10:23",
          code: 1,
          name: "James Washington",
          rank: "Capitan 3",
          distance: "23.11 km",
        },
        {
          id: Math.random(),
          time: "10:23",
          code: 1,
          name: "James Washington",
          rank: "Capitan 3",
          distance: "23.11 km",
        },
        {
          id: Math.random(),
          time: "10:23",
          code: 1,
          name: "James Washington",
          rank: "Capitan 3",
          distance: "23.11 km",
        },
        {
          id: Math.random(),
          time: "10:23",
          code: 1,
          name: "James Washington",
          rank: "Capitan 3",
          distance: "23.11 km",
        },
        {
          id: Math.random(),
          time: "10:23",
          code: 1,
          name: "James Washington",
          rank: "Capitan 3",
          distance: "23.11 km",
        },
        {
          id: Math.random(),
          time: "10:23",
          code: 1,
          name: "James Washington",
          rank: "Capitan 3",
          distance: "23.11 km",
        },
        {
          id: Math.random(),
          time: "10:23",
          code: 1,
          name: "James Washington",
          rank: "Capitan 3",
          distance: "23.11 km",
        },
        {
          id: Math.random(),
          time: "10:23",
          code: 1,
          name: "James Washington",
          rank: "Capitan 3",
          distance: "23.11 km",
        },
        {
          id: Math.random(),
          time: "10:23",
          code: 1,
          name: "James Washington",
          rank: "Capitan 3",
          distance: "23.11 km",
        },
        {
          id: Math.random(),
          time: "10:23",
          code: 1,
          name: "James Washington",
          rank: "Capitan 3",
          distance: "23.11 km",
        },
        {
          id: Math.random(),
          time: "10:23",
          code: 1,
          name: "James Washington",
          rank: "Capitan 3",
          distance: "23.11 km",
        },
        {
          id: Math.random(),
          time: "10:23",
          code: 1,
          name: "James Washington",
          rank: "Capitan 3",
          distance: "23.11 km",
        },
        {
          id: Math.random(),
          time: "10:23",
          code: 1,
          name: "James Washington",
          rank: "Capitan 3",
          distance: "23.11 km",
        },
        {
          id: Math.random(),
          time: "10:23",
          code: 1,
          name: "James Washington",
          rank: "Capitan 3",
          distance: "23.11 km",
        },
        {
          id: Math.random(),
          time: "10:23",
          code: 1,
          name: "James Washington",
          rank: "Capitan 3",
          distance: "23.11 km",
        },
        {
          id: Math.random(),
          time: "10:23",
          code: 1,
          name: "James Washington",
          rank: "Capitan 3",
          distance: "23.11 km",
        },
        {
          id: Math.random(),
          time: "10:23",
          code: 1,
          name: "James Washington",
          rank: "Capitan 3",
          distance: "23.11 km",
        },
        {
          id: Math.random(),
          time: "10:23",
          code: 1,
          name: "James Washington",
          rank: "Capitan 3",
          distance: "23.11 km",
        },
      ],
    };
  },
  methods: {
    Delete(id) {
      this.callList = this.callList.filter((el) => el.id !== id);
    },
  },
};
</script>

<style scoped>
@import url("https://fonts.googleapis.com/css2?family=Montserrat:ital,wght@1,600&display=swap");
@import "./Home.css";
</style>
