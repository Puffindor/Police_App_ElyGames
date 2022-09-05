<template>
  <div v-if="active">
    <Login
      :PlayerProfile="PlayerProfile"
      @cl="switchPage"
      v-if="Login === false"
    />
    <div class="app1" v-if="Login === true">
      <div class="header">
        <UpperPplate
          @search="Search"
          @cl="switchPage"
          @status="Status"
          :PlayerProfile="PlayerProfile"
        />
      </div>
      <span>{{ RankAgent }}</span>
      <Sidebar @cl="switchPage" :currentPageID="currentPageID" />

      <div class="content1">
        <component
          @back="switchPage"
          @ItemID="profile"
          @AgentID="agent_profile"
          @cl="switchPage"
          @invited="Invited"
          @upload="Upload"
          @upload_player="UploadPlayer"
          @deleteCall="deleteCall"
          @rank="ranks"
          @add_car="AddCar"
          @agent_rank="AgentRank"
          :ranks="this.Ranks"
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
          :CitizensCallList="CitizensCallList"
        ></component>
      </div>
    </div>
  </div>
</template>

<script>
import Home from "./components/Pages/Home/Home.vue";
import Criminal_files from "./components/Pages/Criminal Files/Criminal_files.vue";
import Criminal_profile from "./components/Pages/Criminal Files/Criminal_profile.vue";
import Agent_profile from "./components/Pages/Agents/Agent_profile.vue";
import CallList from "./components/Pages/Calls/CallList.vue";
import Sidebar from "./components/UI/Sidebar.vue";
import UpperPplate from "./components/UI/UpperPplate.vue";
import Search from "./components/UI/Search.vue";
import Login from "./components/Player/Login.vue";
import Stuff from "./components/Pages/Inventory/Stuff.vue";
import Player_profile from "./components/Player/Player_profile.vue";
import Agents from "./components/Pages/Agents/Agents.vue";
import Cars from "./components/Pages/Cars/Cars.vue";

export default {
  emits: [
    "back",
    "ItemID",
    "AgentID",
    "cl",
    "invited",
    "upload",
    "upload_player",
    "deleteCall",
  ],
  components: {
    Home,
    Criminal_files,
    Criminal_profile,
    Agent_profile,
    CallList,
    Sidebar,
    UpperPplate,
    Search,
    Login,
    Stuff,
    Player_profile,
    Agents,
    Cars,
  },
  data() {
    return {
      Rank_agent: "",
      possibleRanks: [],

      CarAdded: false,
      Login: true,
      index_agent: 0,
      name: "Home",
      index: 1,
      currentPageID: 1,
      SearchResalut: [],
      SearchInput1: this.SearchInput,
      CitizensCallList: [
        {
          id: Math.random(),
          name: "James brown",
          time: "10:22",
          massage: "HELP ME, THEY WANT TO KILL ME!!!!!!",
          distance: "1.5km",
        },
        {
          id: Math.random(),
          name: "James brown",
          time: "10:22",
          massage: "HELP ME, THEY WANT TO KILL ME!!!!!!",
          distance: "1.5km",
        },
        {
          id: Math.random(),
          name: "James brown",
          time: "10:22",
          massage: "HELP ME, THEY WANT TO KILL ME!!!!!!",
          distance: "1.5km",
        },
        {
          id: Math.random(),
          name: "James brown",
          time: "10:22",
          massage: "HELP ME, THEY WANT TO KILL ME!!!!!!",
          distance: "1.5km",
        },
        {
          id: Math.random(),
          name: "James brown",
          time: "10:22",
          massage: "HELP ME, THEY WANT TO KILL ME!!!!!!",
          distance: "1.5km",
        },
        {
          id: Math.random(),
          name: "James brown",
          time: "10:22",
          massage: "HELP ME, THEY WANT TO KILL ME!!!!!!",
          distance: "1.5km",
        },
        {
          id: Math.random(),
          name: "James brown",
          time: "10:22",
          massage: "HELP ME, THEY WANT TO KILL ME!!!!!!",
          distance: "1.5km",
        },
        {
          id: Math.random(),
          name: "James brown",
          time: "10:22",
          massage: "HELP ME, THEY WANT TO KILL ME!!!!!!",
          distance: "1.5km",
        },
        {
          id: Math.random(),
          name: "James brown",
          time: "10:22",
          massage: "HELP ME, THEY WANT TO KILL ME!!!!!!",
          distance: "1.5km",
        },
        {
          id: Math.random(),
          name: "James brown",
          time: "10:22",
          massage: "HELP ME, THEY WANT TO KILL ME!!!!!!",
          distance: "1.5km",
        },
        {
          id: Math.random(),
          name: "James brown",
          time: "10:22",
          massage: "HELP ME, THEY WANT TO KILL ME!!!!!!",
          distance: "1.5km",
        },
        {
          id: Math.random(),
          name: "James brown",
          time: "10:22",
          massage: "HELP ME, THEY WANT TO KILL ME!!!!!!",
          distance: "1.5km",
        },
        {
          id: Math.random(),
          name: "James brown",
          time: "10:22",
          massage: "HELP ME, THEY WANT TO KILL ME!!!!!!",
          distance: "1.5km",
        },
        {
          id: Math.random(),
          name: "James brown",
          time: "10:22",
          massage: "HELP ME, THEY WANT TO KILL ME!!!!!!",
          distance: "1.5km",
        },
        {
          id: Math.random(),
          name: "James brown",
          time: "10:22",
          massage: "HELP ME, THEY WANT TO KILL ME!!!!!!",
          distance: "1.5km",
        },
        {
          id: Math.random(),
          name: "James brown",
          time: "10:22",
          massage: "HELP ME, THEY WANT TO KILL ME!!!!!!",
          distance: "1.5km",
        },
        {
          id: Math.random(),
          name: "James brown",
          time: "10:22",
          massage: "HELP ME, THEY WANT TO KILL ME!!!!!!",
          distance: "1.5km",
        },
        {
          id: Math.random(),
          name: "James brown",
          time: "10:22",
          massage: "HELP ME, THEY WANT TO KILL ME!!!!!!",
          distance: "1.5km",
        },
        {
          id: Math.random(),
          name: "James brown",
          time: "10:22",
          massage: "HELP ME, THEY WANT TO KILL ME!!!!!!",
          distance: "1.5km",
        },
        {
          id: Math.random(),
          name: "James brown",
          time: "10:22",
          massage: "HELP ME, THEY WANT TO KILL ME!!!!!!",
          distance: "1.5km",
        },
        {
          id: Math.random(),
          name: "James brown",
          time: "10:22",
          massage: "HELP ME, THEY WANT TO KILL ME!!!!!!",
          distance: "1.5km",
        },
        {
          id: Math.random(),
          name: "James brown",
          time: "10:22",
          massage: "HELP ME, THEY WANT TO KILL ME!!!!!!",
          distance: "1.5km",
        },
        {
          id: Math.random(),
          name: "Billy brown",
          time: "10:22",
          massage: "HELP ME, THEY WANT TO KILL ME!!!!!!",
          distance: "1.5km",
        },
        {
          id: Math.random(),
          name: "James brown",
          time: "10:22",
          massage: "HELP ME, THEY WANT TO KILL ME!!!!!!",
          distance: "1.5km",
        },
        {
          id: Math.random(),
          name: "Jack brown",
          time: "10:22",
          massage: "HELP ME, THEY WANT TO KILL ME!!!!!!",
          distance: "1.5km",
        },
      ],
      CriminalList: [
        {
          id: Math.floor(Math.random() * (999 - 1)) + 1,
          Fistname: "Billy",
          Lastname: "Williams",
          sex: "male",
          birthday: "21.01.2021",
          phone: "454 - 0000",
          record: 1,
          height: "1.89m",
          age: 19,
          addres: "Nope",
          ethnicity: "Afro-moldave",
          otherInfo: "This has nothing to do with the criminal records. a.",
          history: [],
        },
        {
          id: Math.floor(Math.random() * (999 - 1)) + 1,
          Fistname: "Billy",
          Lastname: "Williams",
          sex: "male",
          birthday: "21.01.2021",
          phone: "454 - 0000",
          record: 1,
          height: "1.89m",
          age: 19,
          addres: "Nope",
          ethnicity: "Afro-moldave",
          otherInfo: "This has nothing to do with the criminal records. a.",
          history: [],
        },
        {
          id: Math.floor(Math.random() * (999 - 1)) + 1,
          Fistname: "Billy",
          Lastname: "Williams",
          sex: "male",
          birthday: "21.01.2021",
          phone: "454 - 0000",
          record: 1,
          height: "1.89m",
          age: 19,
          addres: "Nope",
          ethnicity: "Afro-moldave",
          otherInfo: "This has nothing to do with the criminal records. a.",
          history: [],
        },
        {
          id: Math.floor(Math.random() * (999 - 1)) + 1,
          Fistname: "Billy",
          Lastname: "Williams",
          sex: "male",
          birthday: "21.01.2021",
          phone: "454 - 0000",
          record: 1,
          height: "1.89m",
          age: 19,
          addres: "Nope",
          ethnicity: "Afro-moldave",
          otherInfo: "This has nothing to do with the criminal records. a.",
          history: [],
        },
        {
          id: Math.floor(Math.random() * (999 - 1)) + 1,
          Fistname: "Billy",
          Lastname: "Williams",
          sex: "male",
          birthday: "21.01.2021",
          phone: "454 - 0000",
          record: 1,
          height: "1.89m",
          age: 19,
          addres: "Nope",
          ethnicity: "Afro-moldave",
          otherInfo: "This has nothing to do with the criminal records. a.",
          history: [],
        },
        {
          id: Math.floor(Math.random() * (999 - 1)) + 1,
          Fistname: "Billy",
          Lastname: "Williams",
          sex: "male",
          birthday: "21.01.2021",
          phone: "454 - 0000",
          record: 1,
          height: "1.89m",
          age: 19,
          addres: "Nope",
          ethnicity: "Afro-moldave",
          otherInfo: "This has nothing to do with the criminal records. a.",
          history: [],
        },
        {
          id: Math.floor(Math.random() * (999 - 1)) + 1,
          Fistname: "Billy",
          Lastname: "Williams",
          sex: "male",
          birthday: "21.01.2021",
          phone: "454 - 0000",
          record: 1,
          height: "1.89m",
          age: 19,
          addres: "Nope",
          ethnicity: "Afro-moldave",
          otherInfo: "This has nothing to do with the criminal records. a.",
          history: [],
        },
        {
          id: Math.floor(Math.random() * (999 - 1)) + 1,
          Fistname: "Billy",
          Lastname: "Williams",
          sex: "male",
          birthday: "21.01.2021",
          phone: "454 - 0000",
          record: 1,
          height: "1.89m",
          age: 19,
          addres: "Nope",
          ethnicity: "Afro-moldave",
          otherInfo: "This has nothing to do with the criminal records. a.",
          history: [],
        },
        {
          id: Math.floor(Math.random() * (999 - 1)) + 1,
          Fistname: "Billy",
          Lastname: "Williams",
          sex: "male",
          birthday: "21.01.2021",
          phone: "454 - 0000",
          record: 1,
          height: "1.89m",
          age: 19,
          addres: "Nope",
          ethnicity: "Afro-moldave",
          otherInfo: "This has nothing to do with the criminal records. a.",
          history: [],
        },
        {
          id: Math.floor(Math.random() * (999 - 1)) + 1,
          Fistname: "Billy",
          Lastname: "Williams",
          sex: "male",
          birthday: "21.01.2021",
          phone: "454 - 0000",
          record: 1,
          height: "1.89m",
          age: 19,
          addres: "Nope",
          ethnicity: "Afro-moldave",
          otherInfo: "This has nothing to do with the criminal records. a.",
          history: [],
        },
        {
          id: Math.floor(Math.random() * (999 - 1)) + 1,
          Fistname: "Billy",
          Lastname: "Williams",
          sex: "male",
          birthday: "21.01.2021",
          phone: "454 - 0000",
          record: 1,
          height: "1.89m",
          age: 19,
          addres: "Nope",
          ethnicity: "Afro-moldave",
          otherInfo: "This has nothing to do with the criminal records. a.",
          history: [],
        },
        {
          id: Math.floor(Math.random() * (999 - 1)) + 1,
          Fistname: "Billy",
          Lastname: "Williams",
          sex: "male",
          birthday: "21.01.2021",
          phone: "454 - 0000",
          record: 1,
          height: "1.89m",
          age: 19,
          addres: "Nope",
          ethnicity: "Afro-moldave",
          otherInfo: "This has nothing to do with the criminal records. a.",
          history: [],
        },
        {
          id: Math.floor(Math.random() * (999 - 1)) + 1,
          Fistname: "Billy",
          Lastname: "Williams",
          sex: "male",
          birthday: "21.01.2021",
          phone: "454 - 0000",
          record: 1,
          height: "1.89m",
          age: 19,
          addres: "Nope",
          ethnicity: "Afro-moldave",
          otherInfo: "This has nothing to do with the criminal records. a.",
          history: [],
        },
        {
          id: Math.floor(Math.random() * (999 - 1)) + 1,
          Fistname: "Billy",
          Lastname: "Williams",
          sex: "male",
          birthday: "21.01.2021",
          phone: "454 - 0000",
          record: 1,
          height: "1.89m",
          age: 19,
          addres: "Nope",
          ethnicity: "Afro-moldave",
          otherInfo: "This has nothing to do with the criminal records. a.",
          history: [],
        },
        {
          id: Math.floor(Math.random() * (999 - 1)) + 1,
          Fistname: "Billy",
          Lastname: "Williams",
          sex: "male",
          birthday: "21.01.2021",
          phone: "454 - 0000",
          record: 1,
          height: "1.89m",
          age: 19,
          addres: "Nope",
          ethnicity: "Afro-moldave",
          otherInfo: "This has nothing to do with the criminal records. a.",
          history: [],
        },
        {
          id: Math.floor(Math.random() * (999 - 1)) + 1,
          Fistname: "Billy",
          Lastname: "Williams",
          sex: "male",
          birthday: "21.01.2021",
          phone: "454 - 0000",
          record: 1,
          height: "1.89m",
          age: 19,
          addres: "Nope",
          ethnicity: "Afro-moldave",
          otherInfo: "This has nothing to do with the criminal records. a.",
          history: [],
        },
        {
          id: Math.floor(Math.random() * (999 - 1)) + 1,
          Fistname: "Billy",
          Lastname: "Williams",
          sex: "male",
          birthday: "21.01.2021",
          phone: "454 - 0000",
          record: 1,
          height: "1.89m",
          age: 19,
          addres: "Nope",
          ethnicity: "Afro-moldave",
          otherInfo: "This has nothing to do with the criminal records. a.",
          history: [],
        },
        {
          id: Math.floor(Math.random() * (999 - 1)) + 1,
          Fistname: "Billy",
          Lastname: "Williams",
          sex: "male",
          birthday: "21.01.2021",
          phone: "454 - 0000",
          record: 1,
          height: "1.89m",
          age: 19,
          addres: "Nope",
          ethnicity: "Afro-moldave",
          otherInfo: "This has nothing to do with the criminal records. a.",
          history: [],
        },
        {
          id: Math.floor(Math.random() * (999 - 1)) + 1,
          Fistname: "Billy",
          Lastname: "Williams",
          sex: "male",
          birthday: "21.01.2021",
          phone: "454 - 0000",
          record: 1,
          height: "1.89m",
          age: 19,
          addres: "Nope",
          ethnicity: "Afro-moldave",
          otherInfo: "This has nothing to do with the criminal records. a.",
          history: [],
        },
        {
          id: Math.floor(Math.random() * (999 - 1)) + 1,
          Fistname: "Billy",
          Lastname: "Williams",
          sex: "male",
          birthday: "21.01.2021",
          phone: "454 - 0000",
          record: 1,
          height: "1.89m",
          age: 19,
          addres: "Nope",
          ethnicity: "Afro-moldave",
          otherInfo: "This has nothing to do with the criminal records. a.",
          history: [],
        },
        {
          id: Math.floor(Math.random() * (999 - 1)) + 1,
          Fistname: "Billy",
          Lastname: "Williams",
          sex: "male",
          birthday: "21.01.2021",
          phone: "454 - 0000",
          record: 1,
          height: "1.89m",
          age: 19,
          addres: "Nope",
          ethnicity: "Afro-moldave",
          otherInfo: "This has nothing to do with the criminal records. a.",
          history: [],
        },
        {
          id: Math.floor(Math.random() * (999 - 1)) + 1,
          Fistname: "Billy",
          Lastname: "Williams",
          sex: "male",
          birthday: "21.01.2021",
          phone: "454 - 0000",
          record: 1,
          height: "1.89m",
          age: 19,
          addres: "Nope",
          ethnicity: "Afro-moldave",
          otherInfo: "This has nothing to do with the criminal records. a.",
          history: [],
        },
        {
          id: Math.floor(Math.random() * (999 - 1)) + 1,
          Fistname: "Billy",
          Lastname: "Williams",
          sex: "male",
          birthday: "21.01.2021",
          phone: "454 - 0000",
          record: 1,
          height: "1.89m",
          age: 19,
          addres: "Nope",
          ethnicity: "Afro-moldave",
          otherInfo: "This has nothing to do with the criminal records. a.",
          history: [],
        },
        {
          id: Math.floor(Math.random() * (999 - 1)) + 1,
          Fistname: "Billy",
          Lastname: "Williams",
          sex: "male",
          birthday: "21.01.2021",
          phone: "454 - 0000",
          record: 1,
          height: "1.89m",
          age: 19,
          addres: "Nope",
          ethnicity: "Afro-moldave",
          otherInfo: "This has nothing to do with the criminal records. a.",
          history: [],
        },
        {
          id: Math.floor(Math.random() * (999 - 1)) + 1,
          Fistname: "Billy",
          Lastname: "Williams",
          sex: "male",
          birthday: "21.01.2021",
          phone: "454 - 0000",
          record: 1,
          height: "1.89m",
          age: 19,
          addres: "Nope",
          ethnicity: "Afro-moldave",
          otherInfo: "This has nothing to do with the criminal records. a.",
          history: [],
        },
        {
          id: Math.floor(Math.random() * (999 - 1)) + 1,
          Fistname: "Billy",
          Lastname: "Williams",
          sex: "male",
          birthday: "21.01.2021",
          phone: "454 - 0000",
          record: 1,
          height: "1.89m",
          age: 19,
          addres: "Nope",
          ethnicity: "Afro-moldave",
          otherInfo: "This has nothing to do with the criminal records. a.",
          history: [],
        },
        {
          id: Math.floor(Math.random() * (999 - 1)) + 1,
          Fistname: "Billy",
          Lastname: "Williams",
          sex: "male",
          birthday: "21.01.2021",
          phone: "454 - 0000",
          record: 1,
          height: "1.89m",
          age: 19,
          addres: "Nope",
          ethnicity: "Afro-moldave",
          otherInfo: "This has nothing to do with the criminal records. a.",
          history: [],
        },
        {
          id: Math.floor(Math.random() * (999 - 1)) + 1,
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
          id: Math.floor(Math.random() * (999 - 1)) + 1,
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
          id: Math.floor(Math.random() * (999 - 1)) + 1,
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
          id: Math.floor(Math.random() * (999 - 1)) + 1,
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
          id: Math.floor(Math.random() * (999 - 1)) + 1,
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
          id: Math.floor(Math.random() * (999 - 1)) + 1,
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
          id: Math.floor(Math.random() * (999 - 1)) + 1,
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
          id: Math.floor(Math.random() * (999 - 1)) + 1,
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
          id: Math.floor(Math.random() * (999 - 1)) + 1,
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
          exp: 300,
          avatar:
            "https://cs.pikabu.ru/post_img/2013/04/03/1/1364939641_2143669487.jpg",
          id: Math.floor(Math.random() * (999 - 1)) + 1,
          name: "Jhon Wiliams",
          rank: "",
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
              name: "Robbery in city",
              status: "Complited",
            },
            {
              name: "Robbery in city",
              status: "Complited",
            },
            {
              name: "Robbery in city",
              status: "Complited",
            },
            {
              name: "Robbery in city",
              status: "Complited",
            },
            {
              name: "Robbery in city",
              status: "Complited",
            },
            {
              name: "Robbery in city",
              status: "Complited",
            },
            {
              name: "Robbery in city",
              status: "Complited",
            },
            {
              name: "Robbery in city",
              status: "Complited",
            },
            {
              name: "Robbery in city",
              status: "Complited",
            },
            {
              name: "Robbery in city",
              status: "Complited",
            },
            {
              name: "Robbery in city",
              status: "Complited",
            },
            {
              name: "Robbery in city",
              status: "Complited",
            },
            {
              name: "Robbery in city",
              status: "Complited",
            },
            {
              name: "Robbery in city",
              status: "Complited",
            },
            {
              name: "Robbery in city",
              status: "Complited",
            },
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
          medals: [
            {
              id: Math.random(),
              img: "https://image.shutterstock.com/image-vector/champion-art-golden-medal-red-260nw-685238779.jpg",
            },
            {
              id: Math.random(),
              img: "https://image.shutterstock.com/image-vector/champion-art-golden-medal-red-260nw-685238779.jpg",
            },
            {
              id: Math.random(),
              img: "https://image.shutterstock.com/image-vector/champion-art-golden-medal-red-260nw-685238779.jpg",
            },
            {
              id: Math.random(),
              img: "https://image.shutterstock.com/image-vector/champion-art-golden-medal-red-260nw-685238779.jpg",
            },
            {
              id: Math.random(),
              img: "https://image.shutterstock.com/image-vector/champion-art-golden-medal-red-260nw-685238779.jpg",
            },
            {
              id: Math.random(),
              img: "https://image.shutterstock.com/image-vector/champion-art-golden-medal-red-260nw-685238779.jpg",
            },
            {
              id: Math.random(),
              img: "https://image.shutterstock.com/image-vector/champion-art-golden-medal-red-260nw-685238779.jpg",
            },
            {
              id: Math.random(),
              img: "https://image.shutterstock.com/image-vector/champion-art-golden-medal-red-260nw-685238779.jpg",
            },
            {
              id: Math.random(),
              img: "https://image.shutterstock.com/image-vector/champion-art-golden-medal-red-260nw-685238779.jpg",
            },
            {
              id: Math.random(),
              img: "https://image.shutterstock.com/image-vector/champion-art-golden-medal-red-260nw-685238779.jpg",
            },
            {
              id: Math.random(),
              img: "https://image.shutterstock.com/image-vector/champion-art-golden-medal-red-260nw-685238779.jpg",
            },
            {
              id: Math.random(),
              img: "https://image.shutterstock.com/image-vector/champion-art-golden-medal-red-260nw-685238779.jpg",
            },
          ],
        },
        {
          exp: 50,
          avatar:
            "https://cs.pikabu.ru/post_img/2013/04/03/1/1364939641_2143669487.jpg",
          id: Math.floor(Math.random() * (999 - 1)) + 1,
          name: "Jhon Wiliams",
          rank: "",
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
              name: "Robbery in city",
              status: "Complited",
            },
            {
              name: "Robbery in city",
              status: "Complited",
            },
            {
              name: "Robbery in city",
              status: "Complited",
            },
            {
              name: "Robbery in city",
              status: "Complited",
            },
            {
              name: "Robbery in city",
              status: "Complited",
            },
            {
              name: "Robbery in city",
              status: "Complited",
            },
            {
              name: "Robbery in city",
              status: "Complited",
            },
            {
              name: "Robbery in city",
              status: "Complited",
            },
            {
              name: "Robbery in city",
              status: "Complited",
            },
            {
              name: "Robbery in city",
              status: "Complited",
            },
            {
              name: "Robbery in city",
              status: "Complited",
            },
            {
              name: "Robbery in city",
              status: "Complited",
            },
            {
              name: "Robbery in city",
              status: "Complited",
            },
            {
              name: "Robbery in city",
              status: "Complited",
            },
            {
              name: "Robbery in city",
              status: "Complited",
            },
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
          medals: [
            {
              id: Math.random(),
              img: "https://image.shutterstock.com/image-vector/champion-art-golden-medal-red-260nw-685238779.jpg",
            },
            {
              id: Math.random(),
              img: "https://image.shutterstock.com/image-vector/champion-art-golden-medal-red-260nw-685238779.jpg",
            },
            {
              id: Math.random(),
              img: "https://image.shutterstock.com/image-vector/champion-art-golden-medal-red-260nw-685238779.jpg",
            },
            {
              id: Math.random(),
              img: "https://image.shutterstock.com/image-vector/champion-art-golden-medal-red-260nw-685238779.jpg",
            },
            {
              id: Math.random(),
              img: "https://image.shutterstock.com/image-vector/champion-art-golden-medal-red-260nw-685238779.jpg",
            },
            {
              id: Math.random(),
              img: "https://image.shutterstock.com/image-vector/champion-art-golden-medal-red-260nw-685238779.jpg",
            },
            {
              id: Math.random(),
              img: "https://image.shutterstock.com/image-vector/champion-art-golden-medal-red-260nw-685238779.jpg",
            },
            {
              id: Math.random(),
              img: "https://image.shutterstock.com/image-vector/champion-art-golden-medal-red-260nw-685238779.jpg",
            },
            {
              id: Math.random(),
              img: "https://image.shutterstock.com/image-vector/champion-art-golden-medal-red-260nw-685238779.jpg",
            },
            {
              id: Math.random(),
              img: "https://image.shutterstock.com/image-vector/champion-art-golden-medal-red-260nw-685238779.jpg",
            },
            {
              id: Math.random(),
              img: "https://image.shutterstock.com/image-vector/champion-art-golden-medal-red-260nw-685238779.jpg",
            },
            {
              id: Math.random(),
              img: "https://image.shutterstock.com/image-vector/champion-art-golden-medal-red-260nw-685238779.jpg",
            },
          ],
        },
        {
          exp: 0,
          avatar:
            "https://cs.pikabu.ru/post_img/2013/04/03/1/1364939641_2143669487.jpg",
          id: Math.floor(Math.random() * (999 - 1)) + 1,
          name: "Jhon Wiliams",
          rank: "",
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
              name: "Robbery in city",
              status: "Complited",
            },
            {
              name: "Robbery in city",
              status: "Complited",
            },
            {
              name: "Robbery in city",
              status: "Complited",
            },
            {
              name: "Robbery in city",
              status: "Complited",
            },
            {
              name: "Robbery in city",
              status: "Complited",
            },
            {
              name: "Robbery in city",
              status: "Complited",
            },
            {
              name: "Robbery in city",
              status: "Complited",
            },
            {
              name: "Robbery in city",
              status: "Complited",
            },
            {
              name: "Robbery in city",
              status: "Complited",
            },
            {
              name: "Robbery in city",
              status: "Complited",
            },
            {
              name: "Robbery in city",
              status: "Complited",
            },
            {
              name: "Robbery in city",
              status: "Complited",
            },
            {
              name: "Robbery in city",
              status: "Complited",
            },
            {
              name: "Robbery in city",
              status: "Complited",
            },
            {
              name: "Robbery in city",
              status: "Complited",
            },
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
          medals: [
            {
              id: Math.random(),
              img: "https://image.shutterstock.com/image-vector/champion-art-golden-medal-red-260nw-685238779.jpg",
            },
            {
              id: Math.random(),
              img: "https://image.shutterstock.com/image-vector/champion-art-golden-medal-red-260nw-685238779.jpg",
            },
            {
              id: Math.random(),
              img: "https://image.shutterstock.com/image-vector/champion-art-golden-medal-red-260nw-685238779.jpg",
            },
            {
              id: Math.random(),
              img: "https://image.shutterstock.com/image-vector/champion-art-golden-medal-red-260nw-685238779.jpg",
            },
            {
              id: Math.random(),
              img: "https://image.shutterstock.com/image-vector/champion-art-golden-medal-red-260nw-685238779.jpg",
            },
            {
              id: Math.random(),
              img: "https://image.shutterstock.com/image-vector/champion-art-golden-medal-red-260nw-685238779.jpg",
            },
            {
              id: Math.random(),
              img: "https://image.shutterstock.com/image-vector/champion-art-golden-medal-red-260nw-685238779.jpg",
            },
            {
              id: Math.random(),
              img: "https://image.shutterstock.com/image-vector/champion-art-golden-medal-red-260nw-685238779.jpg",
            },
            {
              id: Math.random(),
              img: "https://image.shutterstock.com/image-vector/champion-art-golden-medal-red-260nw-685238779.jpg",
            },
            {
              id: Math.random(),
              img: "https://image.shutterstock.com/image-vector/champion-art-golden-medal-red-260nw-685238779.jpg",
            },
            {
              id: Math.random(),
              img: "https://image.shutterstock.com/image-vector/champion-art-golden-medal-red-260nw-685238779.jpg",
            },
            {
              id: Math.random(),
              img: "https://image.shutterstock.com/image-vector/champion-art-golden-medal-red-260nw-685238779.jpg",
            },
          ],
        },
      ],
      Inventory: [
        {
          img: require("./Assets/Stick.png"),
          amount: 10,
        },
      ],
      Cars: [
        {
          vehicule: "Car #1",
          name: "billy Brown",
          rank: "Capitan II ",
          health: "80%",
          fuel: "74%",
        },
        {
          vehicule: "Car #1",
          name: "billy Brown",
          rank: "Capitan II ",
          health: "80%",
          fuel: "74%",
        },
        {
          vehicule: "Car #1",
          name: "billy Brown",
          rank: "Capitan II ",
          health: "80%",
          fuel: "74%",
        },
        {
          vehicule: "Car #1",
          name: "billy Brown",
          rank: "Capitan II ",
          health: "80%",
          fuel: "74%",
        },
        {
          vehicule: "Car #1",
          name: "billy Brown",
          rank: "Capitan II ",
          health: "80%",
          fuel: "74%",
        },
        {
          vehicule: "Car #1",
          name: "billy Brown",
          rank: "Capitan II ",
          health: "80%",
          fuel: "74%",
        },
        {
          vehicule: "Car #1",
          name: "billy Brown",
          rank: "Capitan II ",
          health: "80%",
          fuel: "74%",
        },
        {
          vehicule: "Car #1",
          name: "billy Brown",
          rank: "Capitan II ",
          health: "80%",
          fuel: "74%",
        },
        {
          vehicule: "Car #1",
          name: "billy Brown",
          rank: "Capitan II ",
          health: "80%",
          fuel: "74%",
        },
        {
          vehicule: "Car #1",
          name: "billy Brown",
          rank: "Capitan II ",
          health: "80%",
          fuel: "74%",
        },
        {
          vehicule: "Car #1",
          name: "billy Brown",
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
          name: "James Williams",
          action: "-5 Seringues",
        },
        {
          name: "James Williams",
          action: "-5 Seringues",
        },
        {
          name: "James Williams",
          action: "-5 Seringues",
        },
        {
          name: "James Williams",
          action: "-5 Seringues",
        },
        {
          name: "James Williams",
          action: "-5 Seringues",
        },
        {
          name: "James Williams",
          action: "-5 Seringues",
        },
        {
          name: "James Williams",
          action: "-5 Seringues",
        },
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
        id: 0,
        exp: 339,
        name: "Jhon Wiliams",
        Firstname: "Jhon",
        Lastname: "Wiliams",
        rank: "Lieutenant I",
        status: "Do not disturb",
        distance: "2.5Km",
        birthday: "21.01.2002",
        phone: "666-1234",
        login: "james",
        password: "a",
        history: [
          {
            name: "Robbery in city",
            status: "Complited",
          },
          {
            name: "Robbery in city",
            status: "Complited",
          },
          {
            name: "Robbery in city",
            status: "Complited",
          },
          {
            name: "Robbery in city",
            status: "Complited",
          },
          {
            name: "Robbery in city",
            status: "Complited",
          },
          {
            name: "Robbery in city",
            status: "Complited",
          },
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
        medals: [
          {
            id: Math.random(),
            img: "https://image.shutterstock.com/image-vector/champion-art-golden-medal-red-260nw-685238779.jpg",
          },
          {
            id: Math.random(),
            img: "https://image.shutterstock.com/image-vector/champion-art-golden-medal-red-260nw-685238779.jpg",
          },
          {
            id: Math.random(),
            img: "https://image.shutterstock.com/image-vector/champion-art-golden-medal-red-260nw-685238779.jpg",
          },
          {
            id: Math.random(),
            img: "https://image.shutterstock.com/image-vector/champion-art-golden-medal-red-260nw-685238779.jpg",
          },
          {
            id: Math.random(),
            img: "https://image.shutterstock.com/image-vector/champion-art-golden-medal-red-260nw-685238779.jpg",
          },
          {
            id: Math.random(),
            img: "https://image.shutterstock.com/image-vector/champion-art-golden-medal-red-260nw-685238779.jpg",
          },
          {
            id: Math.random(),
            img: "https://image.shutterstock.com/image-vector/champion-art-golden-medal-red-260nw-685238779.jpg",
          },
          {
            id: Math.random(),
            img: "https://image.shutterstock.com/image-vector/champion-art-golden-medal-red-260nw-685238779.jpg",
          },
          {
            id: Math.random(),
            img: "https://image.shutterstock.com/image-vector/champion-art-golden-medal-red-260nw-685238779.jpg",
          },
          {
            id: Math.random(),
            img: "https://image.shutterstock.com/image-vector/champion-art-golden-medal-red-260nw-685238779.jpg",
          },
          {
            id: Math.random(),
            img: "https://image.shutterstock.com/image-vector/champion-art-golden-medal-red-260nw-685238779.jpg",
          },
          {
            id: Math.random(),
            img: "https://image.shutterstock.com/image-vector/champion-art-golden-medal-red-260nw-685238779.jpg",
          },
          {
            id: Math.random(),
            img: "https://image.shutterstock.com/image-vector/champion-art-golden-medal-red-260nw-685238779.jpg",
          },
          {
            id: Math.random(),
            img: "https://image.shutterstock.com/image-vector/champion-art-golden-medal-red-260nw-685238779.jpg",
          },
          {
            id: Math.random(),
            img: "https://image.shutterstock.com/image-vector/champion-art-golden-medal-red-260nw-685238779.jpg",
          },
          {
            id: Math.random(),
            img: "https://image.shutterstock.com/image-vector/champion-art-golden-medal-red-260nw-685238779.jpg",
          },
          {
            id: Math.random(),
            img: "https://image.shutterstock.com/image-vector/champion-art-golden-medal-red-260nw-685238779.jpg",
          },
          {
            id: Math.random(),
            img: "https://image.shutterstock.com/image-vector/champion-art-golden-medal-red-260nw-685238779.jpg",
          },
          {
            id: Math.random(),
            img: "https://image.shutterstock.com/image-vector/champion-art-golden-medal-red-260nw-685238779.jpg",
          },
          {
            id: Math.random(),
            img: "https://image.shutterstock.com/image-vector/champion-art-golden-medal-red-260nw-685238779.jpg",
          },
          {
            id: Math.random(),
            img: "https://image.shutterstock.com/image-vector/champion-art-golden-medal-red-260nw-685238779.jpg",
          },
          {
            id: Math.random(),
            img: "https://image.shutterstock.com/image-vector/champion-art-golden-medal-red-260nw-685238779.jpg",
          },
          {
            id: Math.random(),
            img: "https://image.shutterstock.com/image-vector/champion-art-golden-medal-red-260nw-685238779.jpg",
          },
          {
            id: Math.random(),
            img: "https://image.shutterstock.com/image-vector/champion-art-golden-medal-red-260nw-685238779.jpg",
          },
          {
            id: Math.random(),
            img: "https://image.shutterstock.com/image-vector/champion-art-golden-medal-red-260nw-685238779.jpg",
          },
          {
            id: Math.random(),
            img: "https://image.shutterstock.com/image-vector/champion-art-golden-medal-red-260nw-685238779.jpg",
          },
          {
            id: Math.random(),
            img: "https://image.shutterstock.com/image-vector/champion-art-golden-medal-red-260nw-685238779.jpg",
          },
          {
            id: Math.random(),
            img: "https://image.shutterstock.com/image-vector/champion-art-golden-medal-red-260nw-685238779.jpg",
          },
          {
            id: Math.random(),
            img: "https://image.shutterstock.com/image-vector/champion-art-golden-medal-red-260nw-685238779.jpg",
          },
        ],
      },

      Ranks: [
        { name: "Private", exp: 0, strap: "Lieutenant_2" }, //Ranks must be placed in ascending order, from lowest to highest
        {
          name: "Lieutenant I",
          exp: 50,
          strap: "Lieutenant_1",
        },
        {
          name: "Lieutenant II",
          exp: 150,
          strap: "Lieutenant_2",
        },
        {
          name: "Lieutenant III",
          exp: 250,
          strap: "Lieutenant_2",
        },
        { name: "Capitan", exp: 450, strap: "Lieutenant_2" },
      ],
    };
  },
  methods: {
    AddCar() {
      if (this.CarAdded === false) {
        this.Cars.unshift({
          vehicule: "Car #2",
          name: this.PlayerProfile.name,
          rank: this.PlayerProfile.rank,
          health: "80%",
          fuel: "74%",
        });
      }
      this.CarAdded = true;
    },
    AgentRank(rank, id) {
      this.AgentsList.forEach((el) => {
        if (el.id === id) {
          el.rank = rank;
        }
      });
    },
    ranks(rank) {
      this.PlayerProfile.rank = rank;
    },
    deleteCall(id) {
      this.CitizensCallList = this.CitizensCallList.filter(
        (el) => el.id !== id
      );
    },
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

    switchPage(pageID) {
      this.currentPageID = pageID;
      switch (pageID) {
        case 1:
          this.name = "Home";
          this.Login = true;
          break;
        case 2:
          this.name = "Criminal_files";
          break;
        case 3:
          this.name = "Stuff";

          break;
        case 4:
          this.name = "CallList";
          break;
        case 5:
          this.name = "Agents";
          break;
        case 9:
          this.name = "Criminal_profile";
          break;
        case 7:
          this.name = "Search";
          break;
        case 8:
          this.name = "Agent_profile";
          break;
        case 6:
          this.name = "Cars";
          break;
        case 10:
          this.name = "Player_profile";
          break;
        case 11:
          this.Login = false;
          break;
      }
    },
    profile(id) {
      this.index = this.CriminalList.findIndex((el) => el.id === id);
    },
    agent_profile(id) {
      this.index_agent = this.AgentsList.findIndex((el) => el.id === id);
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
  computed: {
    RankAgent() {
      this.AgentsList.forEach((agent) => {
        this.possibleRanks = this.Ranks.filter((el) => el.exp <= agent.exp);
        return (agent.rank =
          this.possibleRanks[this.possibleRanks.length - 1].name);
      });
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

.app1 {
  display: grid;
  grid-template-areas:
    "header header"
    "sidebar content";
  grid-template-columns: 300px 1fr;
  grid-template-rows: 115px;
  width: 100vw;
  height: 100vh;
}

.content1 {
  grid-area: content;
  background-color: #f9faff;
}
.header {
  height: 115px;
  grid-area: header;
}

.sidebar {
  grid-area: sidebar;
}

@media screen and (max-width: 1401px) {
  .app1 {
    display: grid;
    grid-template-areas:
      "header header"
      "sidebar content";
    grid-template-columns: 300px 1fr;
    grid-template-rows: 115px;
    width: 100vw;
    height: 100vh;
  }
}
@media screen and (min-width: 2048px) {
}
@media screen and (min-width: 3839px) {
  .app1 {
    grid-template-rows: 200px;
    grid-template-columns: 400px 1fr;
  }
}
</style>
