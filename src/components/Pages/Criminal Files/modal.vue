<template>
  <div class="popup">
    <div class="popup_inner">
      <button @click="show" class="btn"><Icon_red_cross /></button>
      <h1>Edit Criminal Files</h1>
      <div class="popup_inner2">
        <div class="left_column">
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
              {{ this.PopupProfile.Fistname }}<Icon_lock />
            </div>
          </div>

          <div class="Lastname">
            <span class="form_item_string">Lastname</span>
            <div class="form_item Lastname">
              {{ this.PopupProfile.Lastname }}<Icon_lock />
            </div>
          </div>

          <div class="Addres">
            <span class="form_item_string">Addres</span>
            <div class="form_item Addres">
              <input
                v-bind:value="this.PopupProfile.addres"
                @input="this.addres = $event.target.value"
              />
            </div>
          </div>

          <div class="id">
            <span class="form_item_string">id</span>
            <div class="form_item id">
              {{ this.PopupProfile.id }}<Icon_lock />
            </div>
          </div>

          <div class="Birthday">
            <span class="form_item_string">Birthday</span>
            <div class="form_item Birthday">
              {{ this.PopupProfile.birthday }}<Icon_lock />
            </div>
          </div>

          <div class="Ethnicity">
            <span class="form_item_string">Ethnicity</span>
            <div class="form_item Ethnicity">
              <input
                v-bind:value="this.PopupProfile.ethnicity"
                @input="this.ethnicity = $event.target.value"
              />
            </div>
          </div>

          <div>
            <span class="form_item_string">Sex</span>
            <div class="form_item Sex">
              {{ this.PopupProfile.sex }}<Icon_lock />
            </div>
          </div>

          <div class="Phone">
            <span class="form_item_string">Phone</span>
            <div class="form_item Phone">
              {{ this.PopupProfile.phone }}<Icon_lock />
            </div>
          </div>

          <div class="Height">
            <span class="form_item_string">Height</span>
            <div class="form_item Height">
              {{ this.PopupProfile.height }}<Icon_lock />
            </div>
          </div>
        </div>
      </div>

      <div class="other_info_container">
        <span class="form_item_string">Other info</span>
        <div class="other_info">
          <textarea
            class="other_info_input"
            v-bind:value="this.PopupProfile.otherInfo"
            @input="this.otherInfo = $event.target.value"
          ></textarea>
          <!-- <input
            class="other_info_input"
            v-bind:value="this.PopupProfile.otherInfo"
            @input="this.otherInfo = $event.target.value"
          /> -->
        </div>
      </div>
      <button @click="Save" class="btn_save">Save</button>
    </div>
  </div>
</template>

<script>
import Icon_red_cross from "@/Assets/icons/Icon_red_cross.vue";
import Icon_lock from "@/Assets/icons/Icon_lock.vue";
import Icon_upload from "@/Assets/icons/Icon_upload.vue";

export default {
  emits: ["upload", "close"],
  data() {
    return {
      avatar: "",
      Link: "",
    };
  },
  components: {
    Icon_lock,
    Icon_upload,
    Icon_red_cross,
  },
  props: ["PopupProfile"],
  ethnicity: "",
  addres: "",
  otherInfo: "",
  methods: {
    Upload() {
      this.$emit("upload", this.Link, this.PopupProfile.id);
      this.Link = "";
    },
    show() {
      this.$emit("close");
    },
    Save() {
      this.$emit("close");
      if (this.ethnicity) {
        this.PopupProfile.ethnicity = this.ethnicity;
      }
      if (this.addres) {
        this.PopupProfile.addres = this.addres;
      }
      if (this.otherInfo) {
        this.PopupProfile.otherInfo = this.otherInfo;
      }
    },
  },
  computed: {
    img() {
      if (this.PopupProfile.avatar) {
        return (this.avatar = this.PopupProfile.avatar);
      } else {
        return (this.avatar = require("@/Assets/icons/base_avatar.png"));
      }
    },
  },
};
</script>

<style scoped>
@import url("https://fonts.googleapis.com/css2?family=Montserrat:ital,wght@1,600&display=swap");

* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

input {
  border-style: hidden;
  outline: none;
  background-color: transparent;
  font-family: "Segoe UI";
  font-size: 16px;
  font-weight: 600;
}

.other_info_input {
  width: 850px;
  height: 150px;
  border-style: hidden;
  outline: none;
  background-color: transparent;
  font-family: "Segoe UI";
  font-size: 16px;
  font-weight: 600;
}

.link_3 {
  font-family: "Segoe UI";
  font-size: 12px;
  font-weight: 600;
  color: #9da8be;
  margin-top: 8px;
}

h1 {
  margin-left: 70px;
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

.left_column {
  margin-right: 30px;
}
.btn_save {
  cursor: pointer;
  font-family: "Montserrat", sans-serif;
  color: white;
  margin-top: 30px;
  margin-bottom: 54px;
  margin-left: 1199px;
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
.img {
  width: 288px;
  height: 288px;
  border-radius: 6px;
}
.form_item_string {
  font-family: Arial;
  font-size: 16px;
  font-weight: 700;
  color: #9da8be;
  margin-bottom: 10px;
}

.other_info {
  padding-left: 15px;
  padding-top: 12px;
  font-family: "Segoe UI";
  font-size: 16px;
  font-weight: 600;
  width: 880px;
  height: 180px;
  background-color: #f0f3f9;
  border-radius: 6px;
}

.other_info_container {
  margin-top: -40px;
  margin-left: 418px;
}

.table {
  display: grid;
  grid-template-columns: 260px 260px 260px;
  row-gap: 30px;
  column-gap: 50px;
  grid-template-rows: 72px 72px 72px;
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

.btn {
  margin-top: 27px;
  margin-left: 1321px;
  display: flex;
  justify-content: center;
  align-items: center;
  border-style: hidden;
  width: 20px;
  height: 20px;
  cursor: pointer;
  background-color: transparent;
}
.popup_inner {
  width: 1368px;
  height: 769px;
  background-color: #ffffff;
  border-radius: 10px;
}

.popup_inner2 {
  margin-left: 70px;
  margin-right: 70px;
  margin-top: 30px;
  display: grid;
  column-gap: 30px;
  grid-template-columns: 320px 880px;
  justify-items: end;
  align-items: start;
  justify-content: space-between;
}

@media screen and (max-width: 1401px) {
  .other_info_input {
    width: 550px;
    height: 140px;
  }

  .popup_inner {
    width: 1058px;
    height: 940px;
  }
  .table {
    display: grid;
    grid-template-columns: 260px 260px;
    grid-template-rows: 72px 72px 72px 72px 200px;
    grid-template-areas: "other other";
  }
  .popup_inner2 {
    grid-template-columns: 320px 400px;
  }
  .other_info {
    width: 570px;
    height: 152px;
    grid-area: other;
  }
  .other_info_container {
    margin-top: -80px;
  }
  .btn_save {
    margin-left: 889px;
  }
  .btn {
    margin-left: 1010px;
  }

  .Name {
    order: -1;
  }
  .Lastname {
    order: 0;
  }
  .id {
    order: 1;
  }
  .Birthday {
    order: 2;
  }
  .Sex {
    order: 3;
  }
  .Phone {
    order: 4;
  }
  .Addres {
    order: 5;
  }

  .Ethnicity {
    order: 6;
  }
  .Height {
    order: 7;
  }
  @media screen and (min-width: 2047px) {
  }
  @media screen and (min-width: 2559px) {
  }

  @media screen and (min-width: 3839px) {
    .popup_inner {
      width: 3000px;
      height: 769px;
      background-color: red;
      border-radius: 10px;
    }
  }

  /* 2048×1080 2K */
  /* 2560x1440 3K */
  /* 3840 Х 2160 */
}
</style>
