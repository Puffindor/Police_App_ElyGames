<template>
  <div>
    <h1>List of Citizen Calls</h1>
    <div class="search_inp">
      <input placeholder="Search" v-model="this.SearchInput" />
      <Icon_search_small />
    </div>
    <div class="list">
      <div>Time</div>
      <div>Name</div>
      <div>Massage</div>

      <div>Distance</div>
    </div>
    <div class="list_container">
      <div class="listItem" v-for="call in Search">
        <CallList_list :call="call" @deleteCall="deleteCall" />
      </div>
    </div>
  </div>
</template>

<script>
import CallList_list from "./CallList_list.vue";
import Icon_search_small from "@/Assets/icons/Icon_search_small.vue";

export default {
  emits: ["deleteCall"],
  components: { CallList_list, Icon_search_small },
  props: ["CitizensCallList"],
  data() {
    return {
      SearchInput: "",
    };
  },
  methods: {
    deleteCall(id) {
      this.$emit("deleteCall", id);
    },
  },
  computed: {
    Search() {
      if (this.SearchInput) {
        return this.CitizensCallList.filter((el) =>
          el.name
            .toLocaleLowerCase()
            .includes(this.SearchInput.toLocaleLowerCase())
        );
      } else {
        return this.CitizensCallList;
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

.list_container {
  display: flex;
  max-height: 680px;
  margin-left: 118px;
  width: 1372px;
}

.listItem {
  font-family: Arial;

  color: #253042;
  font-weight: 700;
  display: grid;
  grid-template-rows: 80px;
  grid-template-columns: 119px 218px 640px 151px 129px 46px 46px;
  font-size: 18px;
  margin-top: 20px;

  width: 1352px;
  align-items: center;
  border-bottom: 1px solid #c6cddf;
  height: 80px;
}

.search_inp {
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding-left: 14px;
  padding-right: 14px;
  margin-top: 17px;
  margin-left: 114px;
  width: 380px;
  height: 53px;
  border-radius: 6px;
  background-color: #e0e4ee;
}

h1 {
  margin-left: 114px;
  margin-top: 60px;
}

.list {
  display: grid;
  grid-template-columns: 119px 218px 640px 60px;
  width: 1000px;
  color: #a1acc0;
  font-family: "Segoe UI";
  font-weight: 500;
  font-size: 18px;
  margin-left: 118px;
  margin-top: 30px;
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
</style>
