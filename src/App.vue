<template>
  <div class="app">
    <ds-nav-bar @changeView="changeView"></ds-nav-bar>
    <home-page v-if="currentView=='home'" :cards="cards" @remove="removeCard" @showView="showView" ></home-page>
    <profile-page v-else-if="currentView=='profile'" :userDetails="userDetails"></profile-page>
    <view-page v-else-if="currentView=='view'" :card="player"></view-page>
  </div>
</template>

<script>
import DsNavBar from "./components/DsNavBar.vue";
import MyAxios from "./custom-config/MyAxios";
import HomePage from "./components/HomePage.vue";
import ProfilePage from "./components/ProfilePage.vue";
import ViewPage from "./components/ViewPage.vue"

export default {
  name: "App",
  data() {
    return({
      cards: [],
      userDetails:{
        first_name: "Parag",
        last_name: "Nukalwar",
        email: "parag.nukalwar@3ds.com",
        mobile: 7007007007
      },
      currentView: "home",
      player:{}
    })
  },
  components: {
    DsNavBar,
    HomePage,
    ProfilePage,
    ViewPage
  },
  mounted() {
    MyAxios.get("/cards")
      .then((response) => {
        this.cards = response.data;
      })
      .catch((error) => {
        console.log(error.data);
      });
  },

  methods:{

    removeCard(id){
      this.cards = this.cards.filter((card)=>{
        return card.id!==id;
      })
    },

    changeView(viewName){
      this.currentView = viewName;
      console.log("changing view")
    },

    updateUser(user){
      this.userDetails=user;
    },

    showView(card){
      this.changeView("view");
      this.player = card;
    }
  }
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
