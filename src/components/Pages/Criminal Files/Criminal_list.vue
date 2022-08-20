<template>
  <div class="list_item">
    <span>{{ id }}</span>
    <span @click="show">{{ `${Fistname} ${Lastname}` }}</span>
    <span>{{ sex }}</span>
    <span>{{ birthday }}</span>
    <span>{{ phone }}</span>
    <span>{{ record }}</span>
    <button @click="ShowModal" class="btn"><Icon_edite /></button>
  </div>
</template>

<script>
import Icon_edite from "@/Assets/icons/Icon_edite.vue";

export default {
  emits: ["close", "ItemID"],
  props: ["id", "Fistname", "Lastname", "sex", "birthday", "phone", "record"],
  components: { Icon_edite },
  methods: {
    ShowModal() {
      this.$emit("close", this.id);
    },

    show() {
      this.$emit("ItemID", this.id);
    },
  },
};
</script>

<style>
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

.btn {
  cursor: pointer;
  display: flex;
  justify-content: center;
  align-items: center;
  border-style: hidden;
  height: 36px;
  width: 36px;
  background-color: #396aff;
  border-radius: 4px;
}

.list_item {
  font-family: Arial;
  color: #253042;
  font-weight: 700;
  display: grid;
  grid-template-columns: 135px 277px 191px 238px 184px 211px 100px;
  margin-left: 114px;

  width: 1352px;
  height: 80px;
  align-items: center;
  border-bottom: 1px solid #c6cddf;
}

@media screen and (max-width: 1401px) {
  .list_item {
    grid-template-columns: 85px 227px 141px 188px 134px 160px 50px;
    width: 980px;
    margin-left: 20px;
  }
}
</style>
