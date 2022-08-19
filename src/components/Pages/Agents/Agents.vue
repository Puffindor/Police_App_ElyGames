<template>
  <div>
    <h1>Online Agents</h1>
    <div class="search_inp">
      <input placeholder="Search" v-model="this.SearchInput" />

      <Icon_search_small />
    </div>
    <div class="list">
      <span>Name<Icon_triangle /></span>
      <span>Rank<Icon_triangle /></span>
      <span>Status<Icon_triangle /></span>
      <span>Distance</span>
    </div>
    <div class="list_container">
      <div v-for="agent in Search">
        <Agents_list
          :name="agent.name"
          :rank="agent.rank"
          :status="agent.status"
          :distance="agent.distance"
          :id="agent.id"
          :invited="agent.invited"
          @AgentID="agent_profile"
          @invited="Invited"
        />
      </div>
    </div>
  </div>
</template>

<script>
import Icon_search_small from "@/icons/Icon_search_small.vue";
import Icon_triangle from "@/icons/Icon_triangle.vue";
import Agents_list from "./Agents_list.vue";
export default {
  emits: ["AgentID", "cl", "invited"],
  components: { Icon_search_small, Icon_triangle, Agents_list },
  props: ["AgentsList"],
  data() {
    return {
      SearchInput: "",
    };
  },
  methods: {
    agent_profile(id) {
      this.$emit("AgentID", id);
      this.$emit("cl", 8);
    },

    Invited(id) {
      this.$emit("invited", id);
    },
  },
  computed: {
    Search() {
      if (this.SearchInput) {
        return this.AgentsList.filter((el) =>
          el.name
            .toLocaleLowerCase()
            .includes(this.SearchInput.toLocaleLowerCase())
        );
      } else {
        return this.AgentsList;
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

input {
  border-style: hidden;
  color: #253042;
  background-color: transparent;
  outline: none;
  font-size: 16px;
  font-family: "Segoe UI";
  font-weight: 600;
}

.list_container {
  margin-left: 114px;
  display: flex;
  overflow: auto;
  max-height: 680px;
  width: 1425px;
}

.list {
  margin-top: 30px;
  color: #a1acc0;
  font-family: "Segoe UI";
  font-weight: 500;
  font-size: 18px;
  margin-left: 114px;
  display: grid;
  grid-template-columns: 241px 197px 635px 206px;
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
  margin-top: 60px;
  margin-left: 114px;
  font-family: Arial;
  font-size: 32px;
  font-weight: 800;
}
@media screen and (max-width: 1401px) {
  .search_inp,
  h1 {
    margin-left: 40px;
  }
  .list {
    margin-left: 40px;
    grid-template-columns: 241px 240px 324px 183px;
  }
  .list_container {
    margin-left: 40px;
    width: 1105px;
  }
}
</style>
