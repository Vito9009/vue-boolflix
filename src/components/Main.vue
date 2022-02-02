<template>
  <div>
      <div class="film-list">
          <ul>
            <li v-for="(element, index) in filmContainer" 
            :key="index">
              <div>Titolo: {{element.title}}</div>
              <div>Titolo originale: {{element.original_title}}</div>
              <div class="flag-container" v-if="element.original_language === 'it'"> Lingua originale: <img src="https://upload.wikimedia.org/wikipedia/commons/thumb/0/03/Flag_of_Italy.svg/1024px-Flag_of_Italy.svg.png" alt=""></div>
              <div class="flag-container" v-else-if="element.original_language === 'en'"> Lingua originale: <img src="https://upload.wikimedia.org/wikipedia/commons/thumb/a/ae/Flag_of_the_United_Kingdom.svg/800px-Flag_of_the_United_Kingdom.svg.png" alt=""></div>
              <div class="flag-container" v-else> Lingua originale: {{element.original_language}} <img src="https://upload.wikimedia.org/wikipedia/commons/thumb/f/f5/Flag_of_Esperanto.svg/1024px-Flag_of_Esperanto.svg.png" alt=""></div>
              <div>Voto: {{element.vote_average}}</div>
            </li>
          </ul>
      </div>
  </div>
</template>

<script>

export default {
  name: 'Main',
  props: {
    filmContainer: Array
  }
}
</script>

<style lang="scss" scoped>

.film-list{
  ul{
    li{
      padding: 20px;
      margin: 5px 0;
      border: 1px solid rgb(0, 0, 0);

      .flag-container{
        img{
          width: 20px;
        }
      }
    }
  }
}
</style>