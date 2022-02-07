<template>
  <div id="app">
    <Header 
    @search2="userSearch" />
  
    <Main 
    :filmContainer="arrayFilm" 
    :stvContainer="arraySTV"/>

  </div>
</template>

<script>
import axios from "axios"
import Header from "./components/Header.vue"
import Main from "./components/Main.vue"


export default {
  name: 'App',
  components: {
    Header,
    Main
  },
  data(){
    return{
      apiUrl: "https://api.themoviedb.org/3/search/movie",
      apiUrlSTV: "https://api.themoviedb.org/3/search/tv",      
      arrayFilm: [],
      arraySTV: [],      
      searchCont: ""
    }
  },
  methods: {
    getFilm: function(){
      axios
      .get(this.apiUrl, {
          params: {
            api_key: "66cd2a8a2ca34c8579719b1d566390d6",
            query: this.searchCont
          }
        })
        .then((response) => {
          this.arrayFilm = response.data.results;

        })
        .catch((error) => {
          console.log(error);
        });
    },
    getSTV: function(){
      axios
      .get(this.apiUrlSTV, {
          params: {
            api_key: "66cd2a8a2ca34c8579719b1d566390d6",
            query: this.searchCont
          }
        })
        .then((response) => {
          this.arraySTV = response.data.results;

        })
        .catch((error) => {
          console.log(error);
        });
    },

    userSearch: function(element){
      this.searchCont = element;
      this.getFilm();
      this.getSTV();
    },
  },
  created: function() {
    this.getFilm();
    this.getSTV();

  }
}
</script>

<style lang="scss">
@import "./assets/global.scss";
@import "./assets/variables.scss";
@import url('https://fonts.googleapis.com/css2?family=Comforter&family=Roboto:ital,wght@0,100;0,300;0,400;0,500;0,700;0,900;1,100;1,300;1,400;1,500;1,700;1,900&display=swap');

body{
  background-color: $boolflixbgcolor;
}
</style>
