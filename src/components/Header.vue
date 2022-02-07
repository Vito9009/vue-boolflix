<template>
  <div>
      <header>
        <div class="logo">
          <img src="../img/boolflix.png" alt="">
        </div>
          <SearchFTV 
          @filterX="this.emitConnection"
          />
      </header>
  </div>
</template>

<script>
import SearchFTV from "./SearchFTV/SearchFTV.vue"

export default {
  name: 'Header',
  components: {
    SearchFTV
  },
  methods: {
    emitConnection: function(element){
      this.$emit('search2', element)
    }

  }
}
</script>

<style lang="scss" scoped>
@import "../assets/variables.scss";

header{
  height: 60px;
  background-color: $boolflixbgcolor;
  display: flex;

  .logo{
    width: 50%;
    display: flex;
    justify-content: flex-start;
    align-items: center;
    padding: 20px;

    img{
      width: 100px;
    }
  }
}
</style>