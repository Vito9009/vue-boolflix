<template>
  <div id="app">
    <Header 
    @search2="userSearch" />
    <div class="no-film">

    </div>
    <Main 
    :filmContainer="arrayFilm" />

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
      arrayFilm: [],
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
    userSearch: function(element){
      this.searchCont = element;
      this.getFilm();
    },
  },
  created: function() {
    this.getFilm();
  }
}
</script>

<style lang="scss">
@import "./assets/global.scss";
@import "./assets/variables.scss";

</style>
