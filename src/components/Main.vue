<template>
  <div>
      <div v-if="filmContainer.length !=0" class="film-stv-list">
        <div >FILM</div>
          <ul>
            <li v-for="(element, index1) in filmContainer" 
            :key="index1">
              <div>Titolo: {{element.title}}</div>
              <div>Titolo originale: {{element.original_title}}</div>
              <div class="flag-container" v-if="element.original_language === 'it'"> Lingua originale: <span class="language-text"> {{element.original_language}} </span> <img src="https://upload.wikimedia.org/wikipedia/commons/thumb/0/03/Flag_of_Italy.svg/1024px-Flag_of_Italy.svg.png" alt=""></div>
              <div class="flag-container" v-else-if="element.original_language === 'en'"> Lingua originale: <span class="language-text"> {{element.original_language}} </span> <img src="https://upload.wikimedia.org/wikipedia/commons/thumb/a/ae/Flag_of_the_United_Kingdom.svg/800px-Flag_of_the_United_Kingdom.svg.png" alt=""></div>
              <div class="flag-container" v-else> Lingua originale: <span class="language-text"> {{element.original_language}} </span> <img src="https://upload.wikimedia.org/wikipedia/commons/thumb/f/f5/Flag_of_Esperanto.svg/1024px-Flag_of_Esperanto.svg.png" alt=""></div>
              <div>Voto: {{element.vote_average}}</div>
            </li>
          </ul>
      </div>

      <div v-if="stvContainer.length !=0" class="film-stv-list">
        <div>Serie TV</div>
          <ul>
            <li v-for="(element, index2) in stvContainer" 
            :key="index2">
              <div>Titolo: {{element.name}}</div>
              <div>Titolo originale: {{element.original_name}}</div>
              <div class="flag-container" v-if="element.original_language === 'it'"> Lingua originale: <span class="language-text"> {{element.original_language}} </span> <img src="https://upload.wikimedia.org/wikipedia/commons/thumb/0/03/Flag_of_Italy.svg/1024px-Flag_of_Italy.svg.png" alt=""></div>
              <div class="flag-container" v-else-if="element.original_language === 'en'"> Lingua originale: <span class="language-text"> {{element.original_language}} </span> <img src="https://upload.wikimedia.org/wikipedia/commons/thumb/a/ae/Flag_of_the_United_Kingdom.svg/800px-Flag_of_the_United_Kingdom.svg.png" alt=""></div>
              <div class="flag-container" v-else> Lingua originale: <span class="language-text"> {{element.original_language}} </span> <img src="https://upload.wikimedia.org/wikipedia/commons/thumb/f/f5/Flag_of_Esperanto.svg/1024px-Flag_of_Esperanto.svg.png" alt=""></div>
              <div>Voto: {{element.vote_average}}</div>
            </li>
          </ul>
      </div>

  </div>
</template>

<script>

export default {
  name: 'Main',
  data() {
    return{
      active: false
    }
  },
  props: {
    filmContainer: Array,
    stvContainer: Array
  }
}
</script>

<style lang="scss" scoped>

.film-stv-list{
  width: 1000px;
  margin: 0 auto;
  ul{
    display: flex;
    flex-wrap: wrap;
    li{
      width: calc((100% / 4) - 10px);
      height: 300px;
      padding: 20px;
      margin: 5px;
      border: 1px solid rgb(0, 0, 0);
      list-style: none;

      div{
        margin-bottom: 20px;
        
        .test{
          width: 30%;

          img{
            width: 100%;
          }
        }

        .language-text{
          text-transform: uppercase;
        }
      }

      .flag-container{
        img{
          width: 20px;
        }
      }
    }
  }
}
</style>