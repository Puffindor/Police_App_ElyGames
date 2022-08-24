<template>
  <div class="wrapper">
    <h1>List of Citizens</h1>
    <div class="search_string">
      <span class="results"
        >Your search results for:
        <span class="search1">"{{ SearchInput }}"</span>
      </span>
    </div>
    <div class="list">
      <span>id</span>
      <span>Name</span>
      <span>Sex</span>
      <span>Birthday</span>
      <span>Phone</span>
      <span>Criminal record</span>
    </div>
    <div class="list_container3">
      <div class="list_item2" v-for="item in SearchResalut">
        <span>{{ item.id }}</span>
        <span>{{ `${item.Fistname} ${item.Lastname}` }}</span>
        <span>{{ item.sex }}</span>
        <span>{{ item.birthday }}</span>
        <span>{{ item.phone }}</span>
        <span>{{ item.record }}</span>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: ["CriminalList", "SearchInput", "SearchResalut"],
};
</script>

<style scoped>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

.list_item2 {
  font-family: Arial;
  color: #253042;
  font-weight: 700;
  display: grid;
  grid-template-columns: 135px 277px 191px 238px 384px 211px;
  margin-left: 114px;

  width: 1352px;
  height: 80px;
  align-items: center;
  border-bottom: 1px solid #c6cddf;
}
.search1 {
  color: #253042;
  font-weight: 700;
}

.search_string {
  margin-left: 114px;
  margin-top: 20px;
  color: #a1acc0;
  font-family: Arial;
  font-size: 18px;
  font-weight: 400;
}
.list {
  margin-top: 30px;
  color: #a1acc0;
  font-family: "Segoe UI";
  font-weight: 500;
  font-size: 18px;
  margin-left: 114px;
  display: grid;
  grid-template-columns: 135px 277px 191px 238px 384px 421px;
}

.list_container3 {
  width: 1550px;
  display: flex;

  justify-content: flex-start;
  flex-wrap: wrap;
  overflow: auto;
  max-height: 750px;
}

h1 {
  margin-left: 114px;
  margin-top: 51px;
}

@media screen and (max-width: 1401px) {
  .list {
    margin-left: 65px;
    grid-template-columns: 85px 227px 141px 184px 134px 200px;
  }
  h1 {
    margin-left: 40px;
  }
  .list_container3 {
    width: 1010px;
    display: flex;
    margin-left: 40px;
    justify-content: flex-start;
    flex-wrap: wrap;
    overflow: auto;
    max-height: 750px;
  }
  .list_item2 {
    grid-template-columns: 85px 227px 141px 188px 134px 160px;
    width: 980px;
    margin-left: 20px;
  }
  .search_string {
    margin-left: 40px;
  }
}
@media screen and (min-width: 2047px) {
  .list_container3 {
    width: 89%;
  }
  /* .list_item2 {
  } */
}
@media screen and (min-width: 2559px) {
  .wrapper {
    width: 100%;
  }
  .list_container3 {
    width: 95%;
    max-height: 75vh;
  }
  .list_item2 {
    width: 93%;
    grid-template-columns: 8% 17% 18.4% 30% 20% 160px;
  }
  .list {
    width: 88%;
    grid-template-columns: 8% 17% 18.4% 30% 17.5% 160px;
  }
}

@media screen and (min-width: 3839px) {
  .wrapper {
    width: 100%;
  }
  .list_container3 {
    width: 95%;
    max-height: 75vh;
  }
  .list_item2 {
    width: 93%;
    grid-template-columns: 8% 17% 18.4% 30% 20% 160px;
    font-size: 23px;
  }
  .list {
    font-size: 23px;
    width: 88%;
    grid-template-columns: 8% 17% 18.4% 30% 17.5% 200px;
  }
  .results {
    font-size: 20px;
  }
}
</style>
