<template>
  <div>
      <div v-if="filmContainer.length !=0" class="film-stv-list">
        <div class="film-stv-section"><h2>Film</h2></div>
          <div class="container-film-stv">
            <ul class="film-stv" v-for="(element, indexFilm) in filmContainer" 
            :key="indexFilm">
              <div class="poster" 
                v-if="!element.poster_path">
                <div class="no-poster">
                  <img src="../img/boolflix.png" alt="">
                  <div><h3>{{element.title}}</h3></div>
                </div>
              </div>
              <img
                v-else
                :src="'https://image.tmdb.org/t/p/w342' + element.poster_path"
                :alt="element.original_title"
                class="poster"
              />
              <li><span class="my_bold">Titolo:</span> {{element.title}}</li>
              <li><span class="my_bold">Titolo originale:</span> {{element.original_title}}</li>
              <li class="flag-container" v-if="element.original_language === 'it'"> <span class="my_bold">Lingua originale:</span> <span class="language-text"> {{element.original_language}} </span> <img src="https://upload.wikimedia.org/wikipedia/commons/thumb/0/03/Flag_of_Italy.svg/1024px-Flag_of_Italy.svg.png" alt=""></li>
              <li class="flag-container" v-else-if="element.original_language === 'en'"><span class="my_bold">Lingua originale:</span> <span class="language-text"> {{element.original_language}} </span> <img src="https://upload.wikimedia.org/wikipedia/commons/thumb/a/ae/Flag_of_the_United_Kingdom.svg/800px-Flag_of_the_United_Kingdom.svg.png" alt=""></li>
              <li class="flag-container" v-else><span class="my_bold">Lingua originale:</span> <span class="language-text"> {{element.original_language}} </span> <img src="https://upload.wikimedia.org/wikipedia/commons/thumb/f/f5/Flag_of_Esperanto.svg/1024px-Flag_of_Esperanto.svg.png" alt=""></li>
              <li><p class="my_bold">Voto:</p>
                <span v-for="(filmfullstar, indexfullstar) in starVoteAverage(element.vote_average)" :key="indexfullstar">
                  <i class="fas fa-star star"></i>
                </span>
                <span v-for="(filmemptystar, indexemptystar) in (5 - starVoteAverage(element.vote_average))" :key="indexemptystar">
                  <i class="far fa-star star"></i>
                </span>
              </li>
              <li><span class="my_bold">Numero voti:</span> {{element.vote_count}}</li>
              <li v-if="element.overview"><p class="overview">Overview: {{element.overview}}</p></li>
            </ul>
          </div>
      </div>

      <div v-if="stvContainer.length !=0" class="film-stv-list">
        <div class="film-stv-section"><h2>Serie TV</h2></div>
          <div class="container-film-stv">
            <ul class="film-stv" v-for="(element, indexStv) in stvContainer" 
            :key="indexStv">
              <div class="poster" 
                v-if="!element.poster_path">
                <div class="no-poster">
                  <img src="../img/boolflix.png" alt="">
                  <div><h3>{{element.name}}</h3></div>
                </div>
              </div>
              <img
                v-else
                :src="'https://image.tmdb.org/t/p/w342' + element.poster_path"
                :alt="element.original_title"
                class="poster"
              />
              <li><span class="my_bold">Titolo:</span> {{element.name}}</li>
              <li><p class="my_bold">Titolo originale:</p> {{element.original_name}}</li>
              <li class="flag-container" v-if="element.original_language === 'it'"> <span class="my_bold">Lingua originale:</span> <span class="language-text"> {{element.original_language}} </span> <img src="https://upload.wikimedia.org/wikipedia/commons/thumb/0/03/Flag_of_Italy.svg/1024px-Flag_of_Italy.svg.png" alt=""></li>
              <li class="flag-container" v-else-if="element.original_language === 'en'"> <span class="my_bold">Lingua originale:</span> <span class="language-text"> {{element.original_language}} </span> <img src="https://upload.wikimedia.org/wikipedia/commons/thumb/a/ae/Flag_of_the_United_Kingdom.svg/800px-Flag_of_the_United_Kingdom.svg.png" alt=""></li>
              <li class="flag-container" v-else><span class="my_bold">Lingua originale:</span> <span class="language-text"> {{element.original_language}} </span> <img src="https://upload.wikimedia.org/wikipedia/commons/thumb/f/f5/Flag_of_Esperanto.svg/1024px-Flag_of_Esperanto.svg.png" alt=""></li>
              <li><span class="my_bold">Voto:</span>
                <span v-for="(stvfullstar, indexfullstar) in starVoteAverage(element.vote_average)" :key="indexfullstar">
                  <i class="fas fa-star star"></i>
                </span>
                <span v-for="(stvemptystar, indexemptystar) in (5 - starVoteAverage(element.vote_average))" :key="indexemptystar">
                  <i class="far fa-star star"></i>
                </span>
              </li>
              <li><span class="my_bold">Numero voti:</span> {{element.vote_count}}</li>
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

    .film-stv-section{
      text-transform: uppercase;
      margin-bottom: 5px;
    }

  .container-film-stv{
    display: flex;
    flex-wrap: wrap;
    margin-bottom: 20px;

    .film-stv{
      width: calc((100% / 4) - 8px);
      height: 300px;
      padding: 30px;
      list-style: none;
      position: relative;
      margin: 5px 4px;
      background-color: $cardbgcolor;
      overflow: hidden;

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
        justify-content: flex-start;
        align-items: center;
        flex-wrap: wrap;
        gap: 10px;
        margin-bottom: 10px;
        font-size: 14px;

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