<template>
  <div class="Home">
    <div class="wrapper">
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
            <span>
              * Support needed. Will be sent only to your department
            </span>
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
      <h1>Call List</h1>
      <div class="list">
        <div>Time<Icon_triangle class="triangle" /></div>
        <div>Code<Icon_triangle class="triangle" /></div>
        <div>Name<Icon_triangle class="triangle" /></div>
        <div>Rank<Icon_triangle class="triangle" /></div>
        <div>Distance<Icon_triangle class="triangle" /></div>
      </div>
      <div class="list_container">
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
  </div>
</template>

<script>
import Sidebar from "./Sidebar.vue";
import UpperPplate from "./UpperPplate.vue";
import Icon_location from "@/icons/Icon_location.vue";
import Icon_cross from "@/icons/Icon_cross.vue";
import Icon_triangle from "@/icons/Icon_triangle.vue";
import Home_list from "./Home_list.vue";
export default {
  components: {
    Sidebar,
    UpperPplate,
    Icon_location,
    Icon_cross,
    Icon_triangle,
    Home_list,
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
      ],
    };
  },
  methods: {
    cl1(pageID) {
      console.log(pageID);
    },
    Delete(id) {
      this.callList = this.callList.filter((el) => el.id !== id);
    },
  },
};
</script>

<style scoped>
@import url("https://fonts.googleapis.com/css2?family=Montserrat:ital,wght@1,600&display=swap");
* {
  margin: 0px;
  padding: 0px;
  box-sizing: border-box;
}

.listItem {
  font-family: Arial;

  color: #253042;
  font-weight: 700;
  display: grid;
  grid-template-rows: 80px;
  grid-template-columns: 140px 105px 276px 439px 153px 130px 46px 46px;
  font-size: 18px;
  margin-top: 20px;

  width: 1352px;
  align-items: center;
  border-bottom: 1px solid #c6cddf;
  height: 80px;
}

h1 {
  margin-top: 39px;
  margin-left: 108px;
  font-family: Arial;
  font-weight: 800;
  font-size: 32px;
  margin-bottom: 42px;
}

.list_container {
  width: 1360px;
  overflow: auto;
  display: flex;
  justify-content: center;
  align-content: flex-start;
  max-height: 530px;
  flex-wrap: wrap;
  margin-left: 134px;
}
.descriptions {
  margin-left: 60px;
  display: flex;
  flex-direction: row;
}

.descrription {
  font-family: "Segoe UI";
  font-size: 14px;
  color: #a1acc0;
  margin-top: 10px;
  margin-left: 76px;
  width: 200px;
}

.codes {
  display: grid;

  grid-template-columns: 279px 279px 279px 279px 279px;
  margin-left: 108px;
  margin-top: 60px;
  width: 1339px;
}

.triangle {
  cursor: pointer;
  margin-left: 8px;
}

.list {
  display: grid;
  grid-template-columns: 140px 105px 276px 439px 153px;
  width: 1000px;
  color: #a1acc0;
  font-family: "Segoe UI";
  font-weight: 500;
  font-size: 18px;
  margin-left: 134px;
}

.code_container {
  color: #396aff;
  display: flex;
  justify-content: center;
  align-items: center;
  width: 231px;
  height: 112px;
  border-radius: 8px;
  background-color: #e1e9ff;
  font-family: "Montserrat", sans-serif;
  font-size: 40px;
}
@media screen and (max-width: 1401px) {
  h1 {
    margin-left: 40px;
  }

  .list {
    grid-template-columns: 140px 105px 276px 220px 153px;
    margin-left: 20px;
  }
  .listItem {
    width: 938px;
    grid-template-columns: 140px 105px 276px 220px 153px 130px 46px 46px;
  }
  .list_container {
    justify-content: flex-start;
    width: 1120px;
    max-height: 520px;
    margin-left: 20px;
    margin-right: 20px;
  }

  .codes {
    margin-left: 40px;
    grid-template-columns: 210px 210px 210px 210px 210px;
    width: 840px;
  }

  .code_container {
    width: 180px;
    font-size: 30px;
    margin-right: 30px;
  }
  .descriptions {
    display: grid;
    grid-template-columns: 175px 175px 175px 175px 175px;
    grid-template-rows: 100px;
    column-gap: 35px;
    margin-left: 30px;
    height: 80px;
  }
  .descrription {
    height: 80px;
    text-align: center;
    margin-left: 0px;
  }
}
</style>
