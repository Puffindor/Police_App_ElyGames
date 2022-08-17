<template>
  <div class="app">
    <div class="header">
      <UpperPplate
        @search="Search"
        @cl="switchPage"
        @status="Status"
        :PlayerProfile="PlayerProfile"
      />
    </div>
    <div class="sidebar">
      <Sidebar @cl="switchPage" :currentPageID="currentPageID" />
    </div>
    <div class="content">
      <component
        @back="switchPage"
        @ItemID="profile"
        @AgentID="agent_profile"
        @cl="switchPage"
        @invited="Invited"
        @upload="Upload"
        :agent_profile="this.AgentsList[index_agent]"
        :CriminalList="this.CriminalList"
        :list="this.CriminalList[this.index]"
        :AgentsList="this.AgentsList"
        :SearchInput="this.SearchInput1"
        :SearchResalut="this.SearchResalut"
        :is="name"
        :inventory="this.Inventory"
        :cars="this.Cars"
        :InventoryHistory="this.InventoryHistory"
        :PlayerProfile="PlayerProfile"
        @upload_player="UploadPlayer"
      ></component>
    </div>
  </div>
</template>

<script>
import Cars from "./components/Cars.vue";
import Search from "./components/Search.vue";
import Stuff from "./components/Stuff.vue";
import UpperPplate from "./components/UpperPplate.vue";
import Sidebar from "./components/Sidebar.vue";
import Home from "./components/Home.vue";
import Criminal_files from "./components/Criminal_files.vue";
import Criminal_profile from "./components/Criminal_profile.vue";
import Agents from "./components/Agents.vue";
import Agent_profile from "./components/Agent_profile.vue";
import Player_profile from "./components/Player_profile.vue";

export default {
  components: {
    UpperPplate,
    Sidebar,
    Home,
    Criminal_files,
    Criminal_profile,
    Stuff,
    Search,
    Agents,
    Agent_profile,
    Cars,
    Player_profile,
  },
  data() {
    return {
      name: "Stuff",
      index: 1,
      currentPageID: 3,
      SearchResalut: [],
      SearchInput1: this.SearchInput,
      CriminalList: [
        {
          id: 112,
          Fistname: "Billy",
          Lastname: "Williams",
          sex: "male",
          birthday: "21.01.2021",
          phone: "454 - 0000",
          record: 0,
          height: "1.89m",
          age: 19,
          addres: "Nope",
          ethnicity: "Afro-moldave",
          otherInfo: "This has nothing to do with the criminal records. a.",
          history: [],
        },
        {
          id: 11,
          Fistname: "James",
          Lastname: "Williams",
          sex: "male",
          birthday: "21.01.2021",
          phone: "555-0000",
          record: 0,
          height: "1.89m",
          age: 19,
          addres: "Nope",
          ethnicity: "Afro-moldave",
          otherInfo: "This has nothing to do with the criminal records. a.",
          history: [],
        },
        {
          id: 22,
          Fistname: "James",
          Lastname: "Williams",
          sex: "male",
          birthday: "21.01.2021",
          phone: "555-0000",
          record: 0,
          height: "1.89m",
          age: 19,
          addres: "Nope",
          ethnicity: "Afro-moldave",
          otherInfo: "This has nothing to do with the criminal records. a.",
          history: [],
        },
        {
          avatar:
            "https://thumbs.dreamstime.com/b/смешной-преступник-с-оружием-42839377.jpg",
          id: 241,
          Fistname: "James",
          Lastname: "Williams",
          sex: "male",
          birthday: "21.01.2021",
          phone: "555-0000",
          record: 10,
          height: "1.89m",
          age: 19,
          addres: "Nope",
          ethnicity: "Afro-moldave",
          otherInfo: "This has nothing to do with the criminal records. a.",
          history: [],
        },
        {
          avatar: "",
          id: 281,
          Fistname: "James",
          Lastname: "Williams",
          sex: "male",
          birthday: "21.01.2021",
          phone: "555-0000",
          record: 10,
          height: "1.89m",
          age: 19,
          addres: "Nope",
          ethnicity: "Afro-moldave",
          otherInfo: "This has nothing to do with the criminal records. a.",
          history: [],
        },
        {
          avatar: "",
          id: 271,
          Fistname: "James",
          Lastname: "Williams",
          sex: "male",
          birthday: "21.01.2021",
          phone: "555-0000",
          record: 10,
          height: "1.89m",
          age: 19,
          addres: "Nope",
          ethnicity: "Afro-moldave",
          otherInfo: "This has nothing to do with the criminal records. a.",
          history: [],
        },
        {
          avatar: "",
          id: 270,
          Fistname: "James",
          Lastname: "Williams",
          sex: "male",
          birthday: "21.01.2021",
          phone: "555-0000",
          record: 10,
          height: "1.89m",
          age: 19,
          addres: "Nope",
          ethnicity: "Afro-moldave",
          otherInfo: "This has nothing to do with the criminal records. a.",
          history: [],
        },
        {
          avatar: "",
          id: 274,
          Fistname: "James",
          Lastname: "Williams",
          sex: "male",
          birthday: "21.01.2021",
          phone: "555-0000",
          record: 10,
          height: "1.89m",
          age: 19,
          addres: "Nope",
          ethnicity: "Afro-moldave",
          otherInfo: "This has nothing to do with the criminal records. a.",
          history: [],
        },
        {
          avatar: "",
          id: 276,
          Fistname: "James",
          Lastname: "Williams",
          sex: "male",
          birthday: "21.01.2021",
          phone: "555-0000",
          record: 10,
          height: "1.89m",
          age: 19,
          addres: "Nope",
          ethnicity: "Afro-moldave",
          otherInfo: "This has nothing to do with the criminal records. a.",
          history: [
            {
              date: "21.01.2000",
              code: "2.3",
              stations: "Vespucci Beach",
              motive: "Vole de voiture",
              term: "1y 3m 0d",
            },
            {
              date: "21.01.2000",
              code: "2.3",
              stations: "Vespucci Beach",
              motive: "Vole de voiture",
              term: "1y 3m 0d",
            },
            {
              date: "21.01.2000",
              code: "2.3",
              stations: "Vespucci Beach",
              motive: "Vole de voiture",
              term: "1y 3m 0d",
            },
          ],
        },
        {
          id: 222,
          Fistname: "jsosh",
          Lastname: "Williams",
          sex: "male",
          birthday: "21.01.2021",
          phone: "555-0000",
          record: 10,
          height: "1.89m",
          age: 19,
          addres: "Nope",
          ethnicity: "Afro-moldave",
          otherInfo:
            "This has nothing to do with the criminal records. Its just something to fill upp this area.",
          history: [
            {
              date: "21.01.2000",
              code: "2.3",
              stations: "Vespucci Beach",
              motive: "Vole de voiture",
              term: "Innocent",
            },
            {
              date: "21.01.2000",
              code: "2.3",
              stations: "Vespucci Beach",
              motive: "Vole de voiture",
              term: "EN JUGEMENT",
            },
            {
              date: "21.01.2000",
              code: "2.3",
              stations: "Vespucci Beach",
              motive: "Vole de voiture",
              term: "1y 3m 0d",
            },
            {
              date: "21.01.2000",
              code: "2.3",
              stations: "Vespucci Beach",
              motive: "Vole de voiture",
              term: "1y 3m 0d",
            },
            {
              date: "21.01.2000",
              code: "2.3",
              stations: "Vespucci Beach",
              motive: "Vole de voiture",
              term: "1y 3m 0d",
            },
            {
              date: "21.01.2000",
              code: "2.3",
              stations: "Vespucci Beach",
              motive: "Vole de voiture",
              term: "1y 3m 0d",
            },
            {
              date: "21.01.2000",
              code: "2.3",
              stations: "Vespucci Beach",
              motive: "Vole de voiture",
              term: "1y 3m 0d",
            },
            {
              date: "21.01.2000",
              code: "2.3",
              stations: "Vespucci Beach",
              motive: "Vole de voiture",
              term: "1y 3m 0d",
            },
            {
              date: "21.01.2000",
              code: "2.3",
              stations: "Vespucci Beach",
              motive: "Vole de voiture",
              term: "1y 3m 0d",
            },
            {
              date: "21.01.2000",
              code: "2.3",
              stations: "Vespucci Beach",
              motive: "Vole de voiture",
              term: "1y 3m 0d",
            },
            {
              date: "21.01.2000",
              code: "2.3",
              stations: "Vespucci Beach",
              motive: "Vole de voiture",
              term: "1y 3m 0d",
            },
          ],
        },
      ],
      AgentsList: [
        {
          avatar:
            "https://cs.pikabu.ru/post_img/2013/04/03/1/1364939641_2143669487.jpg",
          id: 228,
          name: "Jhon Wiliams",
          rank: "Lieutenant I",
          status: "On duty",
          distance: "2.5Km",
          birthday: "21.01.2002",
          phone: "666-1234",
          invited: false,
          history: [
            {
              name: "Robbery in city",
              status: "Complited",
            },
            {
              name: "Murder",
              status: "In  progress",
            },
            {
              name: "Shooting in city",
              status: "Abandonned",
            },
            {
              name: "Shooting in city",
              status: "Abandonned",
            },
            {
              name: "Shooting in city",
              status: "Abandonned",
            },
            {
              name: "Shooting in city",
              status: "Abandonned",
            },
            {
              name: "Shooting in city",
              status: "Abandonned",
            },
            {
              name: "Shooting in city",
              status: "Abandonned",
            },
            {
              name: "Shooting in city",
              status: "Abandonned",
            },
          ],
        },
        {
          avatar: "",
          id: 220,
          name: "Jhon Wiliams",
          rank: "Lieutenant I",
          status: "AFK",
          distance: "2.5Km",
          birthday: "21.01.2002",
          phone: "666-1234",
          invited: false,
          history: [
            {
              name: "Robbery in city",
              status: "Complited",
            },
            {
              name: "Murder",
              status: "In  progress",
            },
            {
              name: "Shooting in city",
              status: "Abandonned",
            },
            {
              name: "Shooting in city",
              status: "Abandonned",
            },
            {
              name: "Shooting in city",
              status: "Abandonned",
            },
            {
              name: "Shooting in city",
              status: "Abandonned",
            },
            {
              name: "Shooting in city",
              status: "Abandonned",
            },
            {
              name: "Shooting in city",
              status: "Abandonned",
            },
            {
              name: "Shooting in city",
              status: "Abandonned",
            },
          ],
        },
        {
          avatar: "",
          id: 224,
          name: "Jhon Wiliams",
          rank: "Lieutenant I",
          status: "Do not disturb",
          distance: "2.5Km",
          birthday: "21.01.2002",
          phone: "666-1234",
          invited: false,
          history: [
            {
              name: "Robbery in city",
              status: "Complited",
            },
            {
              name: "Murder",
              status: "In  progress",
            },
            {
              name: "Shooting in city",
              status: "Abandonned",
            },
            {
              name: "Shooting in city",
              status: "Abandonned",
            },
            {
              name: "Shooting in city",
              status: "Abandonned",
            },
            {
              name: "Shooting in city",
              status: "Abandonned",
            },
            {
              name: "Shooting in city",
              status: "Abandonned",
            },
            {
              name: "Shooting in city",
              status: "Abandonned",
            },
            {
              name: "Shooting in city",
              status: "Abandonned",
            },
          ],
        },
        {
          avatar: "",
          id: 221,
          name: "Jhon Wiliams",
          rank: "Lieutenant I",
          status: "Need a parthner",
          distance: "2.5Km",
          birthday: "21.01.2002",
          phone: "666-1234",
          invited: false,
          history: [
            {
              name: "Robbery in city",
              status: "Complited",
            },
            {
              name: "Murder",
              status: "In  progress",
            },
            {
              name: "Shooting in city",
              status: "Abandonned",
            },
            {
              name: "Shooting in city",
              status: "Abandonned",
            },
            {
              name: "Shooting in city",
              status: "Abandonned",
            },
            {
              name: "Shooting in city",
              status: "Abandonned",
            },
            {
              name: "Shooting in city",
              status: "Abandonned",
            },
            {
              name: "Shooting in city",
              status: "Abandonned",
            },
            {
              name: "Shooting in city",
              status: "Abandonned",
            },
          ],
        },
      ],
      Inventory: [
        {
          img: require("@/components/Assets/Stick.png"),
          amount: 10,
        },
      ],
      Cars: [
        {
          vehicule: "Car #1",
          name: "James Brown",
          rank: "Capitan II ",
          health: "80%",
          fuel: "74%",
        },
        {
          vehicule: "Car #1",
          name: "James Brown",
          rank: "Capitan II ",
          health: "80%",
          fuel: "74%",
        },
        {
          vehicule: "Car #1",
          name: "James Brown",
          rank: "Capitan II ",
          health: "80%",
          fuel: "74%",
        },
        {
          vehicule: "Car #1",
          name: "James Brown",
          rank: "Capitan II ",
          health: "80%",
          fuel: "74%",
        },
        {
          vehicule: "Car #1",
          name: "James Brown",
          rank: "Capitan II ",
          health: "80%",
          fuel: "74%",
        },
        {
          vehicule: "Car #1",
          name: "James Brown",
          rank: "Capitan II ",
          health: "80%",
          fuel: "74%",
        },
        {
          vehicule: "Car #1",
          name: "Mark Brown",
          rank: "Capitan II ",
          health: "80%",
          fuel: "74%",
        },
        {
          vehicule: "Car #1",
          name: "James Brown",
          rank: "Capitan II ",
          health: "80%",
          fuel: "74%",
        },
        {
          vehicule: "Car #1",
          name: "James Brown",
          rank: "Capitan II ",
          health: "80%",
          fuel: "74%",
        },
        {
          vehicule: "Car #1",
          name: "James Brown",
          rank: "Capitan II ",
          health: "80%",
          fuel: "74%",
        },
        {
          vehicule: "Car #1",
          name: "James Brown",
          rank: "Capitan II ",
          health: "80%",
          fuel: "74%",
        },
        {
          vehicule: "Car #1",
          name: "Billy Brown",
          rank: "Capitan II ",
          health: "80%",
          fuel: "74%",
        },
      ],
      InventoryHistory: [
        {
          name: "James Williams",
          action: "-5 Seringues",
        },
        {
          name: "Billy Williams",
          action: "+500 Seringues",
        },
        {
          name: "Billy Williams",
          action: "+500 Seringues",
        },
        {
          name: "Billy Williams",
          action: "+500 Seringues",
        },
        {
          name: "Billy Williams",
          action: "+500 Seringues",
        },
        {
          name: "Billy Williams",
          action: "+500 Seringues",
        },
        {
          name: "Billy Williams",
          action: "+500 Seringues",
        },
        {
          name: "Billy Williams",
          action: "-800 Seringues",
        },
        {
          name: "Billy Williams",
          action: "+500 Seringues",
        },
        {
          name: "Billy Williams",
          action: "+500 Seringues",
        },
        {
          name: "Billy Williams",
          action: "-4500 Seringues",
        },
        {
          name: "Billy Williams",
          action: "-100 Seringues",
        },
      ],
      PlayerProfile: {
        avatar:
          "https://cs.pikabu.ru/post_img/2013/04/03/1/1364939641_2143669487.jpg",
        id: 402,
        name: "Jhon Wiliams",
        Firstname: "Jhon",
        Lastname: "Wiliams",
        rank: "Lieutenant I",
        status: "Do not disturb",
        distance: "2.5Km",
        birthday: "21.01.2002",
        phone: "666-1234",
        history: [
          {
            name: "Robbery in city",
            status: "Complited",
          },
          {
            name: "Murder",
            status: "In  progress",
          },
          {
            name: "Shooting in city",
            status: "Abandonned",
          },
          {
            name: "Shooting in city",
            status: "Abandonned",
          },
          {
            name: "Shooting in city",
            status: "Abandonned",
          },
          {
            name: "Shooting in city",
            status: "Abandonned",
          },
          {
            name: "Shooting in city",
            status: "Abandonned",
          },
          {
            name: "Shooting in city",
            status: "Abandonned",
          },
          {
            name: "Shooting in city",
            status: "Abandonned",
          },
        ],
      },
    };
  },
  methods: {
    Status(id) {
      switch (id) {
        case 1:
          this.PlayerProfile.status = "Need a parthner";
          break;
        case 2:
          this.PlayerProfile.status = "AFK";
          break;
        case 3:
          this.PlayerProfile.status = "Do not disturb";
          break;
        case 4:
          this.PlayerProfile.status = "On duty";
          break;
      }
    },
    Search(SearchInput) {
      if (typeof SearchInput === "string") {
        this.SearchResalut = this.CriminalList.filter(
          (el) =>
            el.Fistname.toLocaleLowerCase().includes(
              SearchInput.toLocaleLowerCase()
            ) || el.phone.includes(SearchInput)
        );
      }

      this.SearchInput1 = SearchInput;
    },
    Invited(id) {
      this.AgentsList[
        this.AgentsList.findIndex((el) => el.id === id)
      ].invited = true;
    },
    cl(id) {
      console.log(id);
    },
    switchPage(pageID) {
      console.log(pageID);
      this.currentPageID = pageID;
      switch (pageID) {
        case 1:
          this.name = "Home";
          break;
        case 2:
          this.name = "Criminal_files";
          break;
        case 3:
          this.name = "Stuff";

          break;
        case 4:
          break;
        case 5:
          this.name = "Agents";
          break;
        case 6:
          this.name = "Criminal_profile";
          break;
        case 7:
          this.name = "Search";
          break;
        case 8:
          this.name = "Agent_profile";
          break;
        case 9:
          this.name = "Cars";
          break;
        case 10:
          this.name = "Player_profile";
          break;
      }
    },
    profile(id) {
      this.index = this.CriminalList.findIndex((el) => el.id === id);
      console.log(this.index);
    },
    agent_profile(id) {
      this.index_agent = this.AgentsList.findIndex((el) => el.id === id);
      console.log(this.index);
    },
    Upload(link, id) {
      this.CriminalList[
        this.CriminalList.findIndex((el) => el.id === id)
      ].avatar = link;
    },
    UploadPlayer(link) {
      this.PlayerProfile.avatar = link;
    },
  },
};
</script>

<style>
* {
  margin: 0px;
  padding: 0px;
  box-sizing: border-box;
}

.app {
  display: flex;
  flex-direction: column;
}

.app {
  display: grid;
  grid-template-areas:
    "header header"
    "sidebar content";
  grid-template-columns: 300px 1fr;
}

.content {
  grid-area: content;
  background-color: #f9faff;
}
.header {
  grid-area: header;
}

.sidebar {
  width: 300px;
  height: 925px;
  background-color: white;
  font-family: "Montserrat";
  font-size: 16px;
  box-shadow: 10px 0px 50px rgba(0, 0, 0, 0.08);
  z-index: 1;
  grid-area: sidebar;
}

@media screen and (max-width: 1401px) {
  .sidebar {
    height: 980px;
  }
}
@media screen and (min-width: 2048px) {
  .sidebar {
    height: 100%;
  }
}
@media screen and (min-width: 2879px) {
  .sidebar {
    height: 1805px;
  }
}
</style>
