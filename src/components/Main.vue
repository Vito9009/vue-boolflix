<template>
  <div>
      <div v-if="filmContainer.length !=0" class="film-stv-list">
        <div >FILM</div>
          <div class="container-film-stv">
            <ul class="film-stv" v-for="(element, indexFilm) in filmContainer" 
            :key="indexFilm">
              <div class="poster" 
                v-if="!element.poster_path"
                v-show="active"
              >Nessuna immagine copertina</div>
              <img
                v-else
                v-show="active"
                :src="'https://image.tmdb.org/t/p/w342' + element.poster_path"
                :alt="element.original_title"
                class="poster"
              />
              <li>Titolo: {{element.title}}</li>
              <li>Titolo originale: {{element.original_title}}</li>
              <li class="flag-container" v-if="element.original_language === 'it'"> Lingua originale: <span class="language-text"> {{element.original_language}} </span> <img src="https://upload.wikimedia.org/wikipedia/commons/thumb/0/03/Flag_of_Italy.svg/1024px-Flag_of_Italy.svg.png" alt=""></li>
              <li class="flag-container" v-else-if="element.original_language === 'en'"> Lingua originale: <span class="language-text"> {{element.original_language}} </span> <img src="https://upload.wikimedia.org/wikipedia/commons/thumb/a/ae/Flag_of_the_United_Kingdom.svg/800px-Flag_of_the_United_Kingdom.svg.png" alt=""></li>
              <li class="flag-container" v-else> Lingua originale: <span class="language-text"> {{element.original_language}} </span> <img src="https://upload.wikimedia.org/wikipedia/commons/thumb/f/f5/Flag_of_Esperanto.svg/1024px-Flag_of_Esperanto.svg.png" alt=""></li>
              <li v-if="element.vote_average">Voto: {{element.vote_average}}
                <span v-for="i in starVoteAverage(element.vote_average)" :key="i">
                  <i class="fas fa-star star"></i>
                </span>
              </li>
              <li v-else>Voto: Nessuna valutazione</li>
            </ul>
          </div>
      </div>

      <div v-if="stvContainer.length !=0" class="film-stv-list">
        <div>Serie TV</div>
          <div class="container-film-stv">
            <ul class="film-stv" v-for="(element, indexStv) in stvContainer" 
            :key="indexStv">
              <div class="poster" 
                v-if="!element.poster_path"
                v-show="active"
                >Nessuna immagine copertina</div>
              <img v-else
                v-show="active"
                :src="'https://image.tmdb.org/t/p/w342' + element.poster_path"
                :alt="element.original_title"
                class="poster"
              />
              <li>Titolo: {{element.name}}</li>
              <li>Titolo originale: {{element.original_name}}</li>
              <li class="flag-container" v-if="element.original_language === 'it'"> Lingua originale: <span class="language-text"> {{element.original_language}} </span> <img src="https://upload.wikimedia.org/wikipedia/commons/thumb/0/03/Flag_of_Italy.svg/1024px-Flag_of_Italy.svg.png" alt=""></li>
              <li class="flag-container" v-else-if="element.original_language === 'en'"> Lingua originale: <span class="language-text"> {{element.original_language}} </span> <img src="https://upload.wikimedia.org/wikipedia/commons/thumb/a/ae/Flag_of_the_United_Kingdom.svg/800px-Flag_of_the_United_Kingdom.svg.png" alt=""></li>
              <li class="flag-container" v-else> Lingua originale: <span class="language-text"> {{element.original_language}} </span> <img src="https://upload.wikimedia.org/wikipedia/commons/thumb/f/f5/Flag_of_Esperanto.svg/1024px-Flag_of_Esperanto.svg.png" alt=""></li>
              <li v-if="element.vote_average">Voto: {{element.vote_average}}
                <span v-for="i in starVoteAverage(element.vote_average)" :key="i">
                  <i class="fas fa-star star"></i>
                </span>
              </li>
              <li v-else>Voto: Nessuna valutazione</li>
            </ul>
          </div> 
      </div>

  </div>
</template>

<script>

export default {
  name: 'Main',
  data() {
    return{
      active: false,
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

.film-stv-list{
  width: 1000px;
  margin: 0 auto;
  .container-film-stv{
    display: flex;
    flex-wrap: wrap;
    .film-stv{
      width: calc((100% / 4) - 10px);
      height: 300px;
      padding: 20px;
      margin: 5px;
      border: 1px solid rgb(0, 0, 0);
      list-style: none;

      .poster{
        height: 100%;
        display: flex;
        justify-content: center;
        align-items: center;
        margin: 0 auto;

        img{
          width: 100%;
          object-fit: cover;
        }
      }
      li{
        display: flex;
        justify-content: space-between;
        margin-bottom: 20px;

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