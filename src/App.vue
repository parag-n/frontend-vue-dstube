<template>
  <div>
    <ds-nav-bar></ds-nav-bar>
    <home-page v-show="currentView=='home'" @changeView="changeView" :cards="cards" @remove="removeCard"></home-page>
    <profile-page v-show="currentView=='profile'" @changeView="changeView" :userDetails="userDetails"></profile-page>
  </div>
</template>

<script>
import DsNavBar from "./components/DsNavBar.vue";
import MyAxios from "./custom-config/MyAxios";
import HomePage from "./components/HomePage.vue";
import ProfilePage from "./components/ProfilePage.vue"

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
      currentView: "home"
    })
  },
  components: {
    DsNavBar,
    HomePage,
    ProfilePage
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
