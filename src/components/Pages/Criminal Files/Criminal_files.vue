<template>
  <div class="content">
    <h1>List of Criminal Files</h1>
    <div class="list">
      <span>id<Icon_triangle /></span>
      <span>Name<Icon_triangle /></span>
      <span>Sex<Icon_triangle /></span>
      <span>Birthday<Icon_triangle /></span>
      <span>Phone</span>
      <span>Criminal record<Icon_triangle /></span>
    </div>
    <div class="list_container">
      <div v-for="(crime, index) in CriminalList.filter((el) => el.record > 0)">
        <Criminal_list
          @ItemID="Profile"
          @close="Show"
          :id="crime.id"
          :Fistname="crime.Fistname"
          :Lastname="crime.Lastname"
          :sex="crime.sex"
          :birthday="crime.birthday"
          :phone="crime.phone"
          :record="crime.record"
        />
      </div>
    </div>

    <Modal
      :PopupProfile="this.CriminalList[this.index]"
      @close="Show"
      @upload="Upload"
      v-if="showModal"
    />
  </div>
</template>

<script>
import Icon_triangle from "@/icons/Icon_triangle.vue";
import Icon_edite from "@/icons/Icon_edite.vue";
import Modal from "./modal.vue";
import Criminal_profile from "./Criminal_profile.vue";
import Criminal_list from "./Criminal_list.vue";
export default {
  emits: ["upload", "cl", "ItemID"],
  props: ["CriminalList"],
  components: {
    Icon_triangle,
    Icon_edite,
    Modal,
    Criminal_profile,
    Criminal_list,
  },

  data() {
    return {
      pageID: 9,
      showModal: false,
      index: 1,
    };
  },
  methods: {
    Upload(link, id) {
      this.$emit("upload", link, id);
    },
    Show(id) {
      this.showModal = !this.showModal;
      this.index = this.CriminalList.findIndex((el) => el.id === id);
    },
    Profile(id) {
      this.index = this.CriminalList.findIndex((el) => el.id === id);
      this.$emit("cl", this.pageID);
      this.$emit("ItemID", id);
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

* {
  margin: 0px;
  padding: 0px;
  box-sizing: border-box;
}

.list_container {
  width: 1500px;
  display: flex;

  justify-content: flex-start;
  flex-wrap: wrap;
  overflow: auto;
  max-height: 750px;
}

.modal {
  width: 1368px;
  height: 769px;
  background-color: #ffffff;
}

.list {
  margin-top: 30px;
  color: #a1acc0;
  font-family: "Segoe UI";
  font-weight: 500;
  font-size: 18px;
  margin-left: 114px;
  display: grid;
  grid-template-columns: 135px 277px 191px 238px 184px 421px;
}

h1 {
  margin-top: 51px;
  margin-left: 114px;
  font-family: Arial;
  font-weight: 1000;
  font-size: 32px;
}
.criminal_files {
  display: grid;
  grid-template-areas:
    "header header"
    "sidebar content";
  grid-template-columns: 300px 1fr;
}

.wrapper {
  grid-area: content;
}
.header {
  grid-area: header;
}
.sidebar {
  width: 300px;
  height: 965px;
  background-color: white;
  font-family: "Montserrat";
  font-weight: 700;

  font-size: 16px;
  box-shadow: 10px 0px 50px rgba(0, 0, 0, 0.08);
  grid-area: sidebar;
}

@media screen and (max-width: 1401px) {
  .list {
    margin-left: 65px;
    grid-template-columns: 85px 227px 141px 184px 134px 200px;
  }
  h1 {
    margin-left: 20px;
  }
  .list_container {
    width: 1010px;
    display: flex;
    margin-left: 45px;
    justify-content: flex-start;
    flex-wrap: wrap;
    overflow: auto;
    max-height: 750px;
  }
}
</style>
