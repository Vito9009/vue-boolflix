<template>
  <div>
      <div v-if="filmContainer.length !=0" class="film-stv-list">
        <div >FILM</div>
          <div class="container-film-stv">
            <ul class="film-stv" v-for="(element, indexFilm) in filmContainer" 
            :key="indexFilm">
              <div class="poster" 
                v-if="!element.poster_path">
                <div class="no-poster">
                  <div>{{element.title}}</div>
                  <img src="../img/boolflix.png" alt="">
                </div>
              </div>
              <img
                v-else
                :src="'https://image.tmdb.org/t/p/w342' + element.poster_path"
                :alt="element.original_title"
                class="poster"
              />
              <li>Titolo: {{element.title}}</li>
              <li>Titolo originale: {{element.original_title}}</li>
              <li class="flag-container" v-if="element.original_language === 'it'"> Lingua originale: <span class="language-text"> {{element.original_language}} </span> <img src="https://upload.wikimedia.org/wikipedia/commons/thumb/0/03/Flag_of_Italy.svg/1024px-Flag_of_Italy.svg.png" alt=""></li>
              <li class="flag-container" v-else-if="element.original_language === 'en'"> Lingua originale: <span class="language-text"> {{element.original_language}} </span> <img src="https://upload.wikimedia.org/wikipedia/commons/thumb/a/ae/Flag_of_the_United_Kingdom.svg/800px-Flag_of_the_United_Kingdom.svg.png" alt=""></li>
              <li class="flag-container" v-else> Lingua originale: <span class="language-text"> {{element.original_language}} </span> <img src="https://upload.wikimedia.org/wikipedia/commons/thumb/f/f5/Flag_of_Esperanto.svg/1024px-Flag_of_Esperanto.svg.png" alt=""></li>
              <li>Voto: {{element.vote_average}}
                <span v-for="filmfullstar in starVoteAverage(element.vote_average)" :key="filmfullstar">
                  <i class="fas fa-star star"></i>
                </span>
                <span v-for="filmemptystar in (5 - starVoteAverage(element.vote_average))" :key="filmemptystar">
                  <i class="far fa-star star"></i>
                </span>
              </li>
              <li>Numero voti: {{element.vote_count}}</li>
              <li v-if="element.overview"><p class="overview">Overview: {{element.overview}}</p></li>
            </ul>
          </div>
      </div>

      <div v-if="stvContainer.length !=0" class="film-stv-list">
        <div>Serie TV</div>
          <div class="container-film-stv">
            <ul class="film-stv" v-for="(element, indexStv) in stvContainer" 
            :key="indexStv">
              <div class="poster" 
                v-if="!element.poster_path">
                <div class="no-poster">
                  <div>{{element.name}}</div>
                  <img src="../img/boolflix.png" alt="">
                </div>
              </div>
              <img
                v-else
                :src="'https://image.tmdb.org/t/p/w342' + element.poster_path"
                :alt="element.original_title"
                class="poster"
              />
              <li>Titolo: {{element.name}}</li>
              <li>Titolo originale: {{element.original_name}}</li>
              <li class="flag-container" v-if="element.original_language === 'it'"> Lingua originale: <span class="language-text"> {{element.original_language}} </span> <img src="https://upload.wikimedia.org/wikipedia/commons/thumb/0/03/Flag_of_Italy.svg/1024px-Flag_of_Italy.svg.png" alt=""></li>
              <li class="flag-container" v-else-if="element.original_language === 'en'"> Lingua originale: <span class="language-text"> {{element.original_language}} </span> <img src="https://upload.wikimedia.org/wikipedia/commons/thumb/a/ae/Flag_of_the_United_Kingdom.svg/800px-Flag_of_the_United_Kingdom.svg.png" alt=""></li>
              <li class="flag-container" v-else> Lingua originale: <span class="language-text"> {{element.original_language}} </span> <img src="https://upload.wikimedia.org/wikipedia/commons/thumb/f/f5/Flag_of_Esperanto.svg/1024px-Flag_of_Esperanto.svg.png" alt=""></li>
              <li>Voto: {{element.vote_average}}
                <span v-for="stvfullstar in starVoteAverage(element.vote_average)" :key="stvfullstar">
                  <i class="fas fa-star star"></i>
                </span>
                <span v-for="stvemptystar in (5 - starVoteAverage(element.vote_average))" :key="stvemptystar">
                  <i class="far fa-star star"></i>
                </span>
              </li>
              <li>Numero voti: {{element.vote_count}}</li>
              <li v-if="element.overview"><p class="overview">Overview: {{element.overview}}</p></li>
            </ul>
          </div> 
      </div>

  </div>
</template>

<script>

export default {
  name: 'Main',
  data(){
    return{

    }
  },
  props: {
    filmContainer: Array,
    stvContainer: Array
  },
  methods: {
    starVoteAverage: function(star) {
      return Math.ceil(star/2);
    }
  }
}
</script>

<style lang="scss" scoped>
@import "../assets/variables.scss";

.film-stv-list{
  width: 1000px;
  margin: 0 auto;
  color: rgb(255, 255, 255);

  .container-film-stv{
    display: flex;
    flex-wrap: wrap;

    .film-stv{
      width: calc((100% / 4) - 2px);
      height: 300px;
      padding: 30px;
      list-style: none;
      position: relative;
      margin: 5px 1px;
      background-color: $cardbgcolor;

      &:hover .poster{
        display: none;
      }

      .poster{
        height: 100%;
        margin: 0 auto;
        position: absolute;
        top: 0;
        right: 0;
        left: 0;
        background-color: $cardbgcolor;
        display: block;

        img{
          width: 100%;
        }

        .no-poster{
          display: flex;
          justify-content: center;
          align-items: center;
          flex-direction: column;
          width: 100%;
          height: 100%;
          padding: 20px;
          text-align: center;

          img{
            width: 80%;
            margin-top: 20px;
          }
        }
      }
      li{
        display: flex;
        justify-content: space-between;
        margin-bottom: 10px;

        img{
          width: 100%;
        }
      }

        .language-text{
          text-transform: uppercase;
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