<template>
  <div class="UpperPlate">
    <div class="logo_container">
      <img src="@/icons/logo_large.png" />
      <strong class="logo_string"> L.S.P.D </strong>
    </div>
    <div class="search">
      <Icon_seacrh @click="OpenSearch" />
      <span class="string"> Search </span>
      <input
        @input="this.SearchInput = $event.target.value"
        v-bind:value="this.SearchInput"
        class="input"
        placeholder="by name of phone"
      />
    </div>
  </div>
</template>

<script>
import Icon_seacrh from "@/icons/Icon_seacrh.vue";

export default {
  components: { Icon_seacrh },
  data() {
    return {
      SearchInput: "",
    };
  },
  input: "",
  methods: {
    OpenSearch() {
      if (this.SearchInput) {
        this.$emit("search", this.SearchInput);

        this.$emit("cl", 7);
        this.SearchInput = "";
      }
    },
  },
};
</script>

<style scoped>
@import url("https://fonts.googleapis.com/css?family=Roboto+Condensed");
@import url("https://fonts.googleapis.com/css2?family=Montserrat:ital,wght@1,600&display=swap");

strong {
  font-family: "Roboto", sans-serif;
  color: white;
}

.input {
  color: white;
  font-size: 22px;
  background-color: transparent;
  border-style: hidden;
  outline: none;
}

.search {
  font-weight: 600;
  font-family: "Segoe UI";
  margin-left: 41px;
  display: grid;
  grid-template-columns: 54px 77px 190px;
  align-items: end;
}

.string {
  font-family: "Segoe UI";
  font-size: 22px;
  color: #ffffff;
}

.logo_string {
  margin-right: 42px;
}

.logo_container {
  font-size: 41px;
  justify-content: space-around;
  width: 300px;
  display: flex;
  align-items: center;
  border-right: solid 1px #1f2632;
}

.UpperPlate {
  display: flex;
  align-items: center;

  width: 100%;
  height: 115px;
  background-color: #121924;
  z-index: 10;
}
</style>
