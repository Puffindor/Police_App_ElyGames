<template>
  <div class="popup">
    <div class="popup_inner">
      <div class="btn_container2">
        <h1>Edit Profile</h1>
        <button @click="Show" class="btn"><Icon_red_cross /></button>
      </div>
      <div class="wrapper">
        <div class="avatar">
          <!-- <div class="img"></div> -->
          <img class="img" :src="img" />
          <div class="link_1">
            <div @click="Upload" class="link_2"><Icon_upload /></div>
            <input
              placeholder="Link"
              @input="this.Link = $event.target.value"
              v-bind:value="this.Link"
            />
          </div>
          <span class="link_3"
            >* Insert a link to a picture of the criminal</span
          >
        </div>
        <div class="table">
          <div class="Name">
            <span class="form_item_string">Name</span>
            <div class="form_item Fistname">
              {{ this.PlayerProfile.Firstname }}<Icon_lock />
            </div>
          </div>

          <div class="Name">
            <span class="form_item_string">Lastname</span>
            <div class="form_item Fistname">
              {{ this.PlayerProfile.Lastname }}<Icon_lock />
            </div>
          </div>

          <div class="Name">
            <span class="form_item_string">Id</span>
            <div class="form_item Fistname">
              {{ this.PlayerProfile.id }}<Icon_lock />
            </div>
          </div>

          <div class="Name">
            <span class="form_item_string">Birthday</span>
            <div class="form_item Fistname">
              {{ this.PlayerProfile.birthday }}<Icon_lock />
            </div>
          </div>

          <div class="Name">
            <span class="form_item_string">Phone</span>
            <div class="form_item Fistname">
              {{ this.PlayerProfile.phone }}<Icon_lock />
            </div>
          </div>
        </div>
      </div>
      <button @click="Save" class="btn_save">Save</button>
    </div>
  </div>
</template>

<script>
import Icon_red_cross from "../../Assets/icons/Icon_red_cross.vue";
import Icon_upload from "../../Assets/icons/Icon_upload.vue";
import Icon_lock from "../../Assets/icons/Icon_lock.vue";

export default {
  emits: ["close", "upload_player"],
  components: {
    Icon_red_cross,
    Icon_upload,
    Icon_lock,
  },
  props: ["PlayerProfile"],
  data() {
    return {
      Link: "",
      avatar: "",
    };
  },
  methods: {
    Save() {
      this.$emit("close");
    },
    Show() {
      this.$emit("close");
    },
    Upload() {
      this.$emit("upload_player", this.Link);
      this.Link = "";
    },
  },
  computed: {
    img() {
      if (this.PlayerProfile.avatar) {
        return (this.avatar = this.PlayerProfile.avatar);
      } else {
        return (this.avatar = require("../../Assets/icons/base_avatar.png"));
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

.table {
  display: grid;
  grid-template-columns: repeat(2, 260px);
  grid-template-rows: repeat(3, 99px);
  column-gap: 50px;
  row-gap: 10px;
}
.form_item_string {
  font-family: Arial;
  font-size: 16px;
  font-weight: 700;
  color: #9da8be;
  margin-bottom: 10px;
}
.btn_save {
  cursor: pointer;
  font-family: "Montserrat", sans-serif;
  color: white;
  margin-top: 45px;
  margin-bottom: 54px;
  margin-left: 900px;
  font-size: 16px;
  font-weight: 700;
  border-style: hidden;
  width: 99px;
  height: 36px;
  background-color: #396aff;
  border-radius: 4px;
  display: flex;
  justify-content: center;
  align-items: center;
}
.link_3 {
  font-family: "Segoe UI";
  font-size: 12px;
  font-weight: 600;
  color: #9da8be;
  margin-top: 8px;
}

.btn_container2 {
  display: grid;
  grid-template-columns: 940px 60px;
  margin-bottom: 30px;
  margin-left: 70px;
  margin-top: 35px;
}

input {
  border-style: hidden;
  outline: none;
  background-color: transparent;
  font-family: "Segoe UI";
  font-size: 16px;
  font-weight: 600;
}

.wrapper {
  display: grid;
  margin-left: 70px;
  grid-template-columns: 288px 1fr;
  column-gap: 60px;
}

.img {
  width: 288px;
  height: 288px;
  border-radius: 6px;
  background-color: aqua;
}
.link_2 {
  cursor: pointer;
  display: flex;
  align-items: center;
  justify-content: center;
  width: 45px;
  height: 45px;
  background-color: #396aff;
  border-radius: 6px 0px 0px 6px;
  margin-right: 15px;
}
.link_1 {
  margin-top: 20px;

  font-family: "Segoe UI";
  font-size: 16px;
  font-weight: 600;
  color: #9da8be;
  display: flex;
  justify-content: flex-start;
  align-items: center;
  width: 288px;
  height: 45px;
  border-radius: 0px 6px 0px 6px;
  background-color: #f0f3f9;
}

.btn {
  display: flex;
  justify-content: center;
  align-items: center;
  border-style: hidden;
  width: 20px;
  height: 20px;
  cursor: pointer;
  background-color: transparent;
}
.popup {
  display: flex;
  justify-content: center;
  align-items: center;
  background-color: rgba(0, 0, 0, 0.5);
  position: fixed;
  left: 0;
  right: 0;
  top: 0;
  bottom: 0;
  z-index: 100;
}

.form_item {
  display: flex;
  align-items: center;
  justify-content: space-between;
  color: #9da8be;
  padding-left: 15px;
  padding-right: 15px;
  font-family: "Segoe UI";
  font-size: 16px;
  font-weight: 600;
  width: 260px;
  height: 45px;
  border-radius: 6px;
  background-color: #f0f3f9;
}
.popup_inner {
  width: 1058px;
  height: 621px;
  border-radius: 10px;
  background-color: white;
}
@media screen and (min-width: 3839px) {
  .popup_inner {
    width: 1668px;
    height: 1069px;
    border-radius: 10px;
  }
  .img {
    width: 500px;
    height: 500px;
  }
  .wrapper {
    grid-template-columns: 500px 1fr;
  }
  .table {
    display: grid;
    grid-template-columns: repeat(2, 460px);
    grid-template-rows: repeat(3, 80px);
    column-gap: 50px;
    row-gap: 110px;
  }
  .form_item {
    width: 100%;
    height: 100%;
    font-size: 23px;
  }
  .form_item_string {
    font-size: 23px;
  }
  .link_1 {
    width: 100%;
    height: 10%;
  }
  input {
    font-size: 23px;
  }
  .link_2 {
    height: 100%;
  }
  .link_3 {
    font-size: 23px;
  }
  .btn_container2 {
    grid-template-columns: 96.5% 1fr;
  }
  .btn_save {
    margin-top: 285px;
    margin-bottom: 54px;
    margin-left: 1500px;
  }
}
</style>
