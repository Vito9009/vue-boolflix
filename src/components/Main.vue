<template>
  <div>
      <div class="film-list">
          <ul>
            <li v-for="(element, index) in filmContainer" 
            :key="index">
            <div>Titolo: {{element.title}}</div>
            <div>Titolo originale: {{element.original_title}}</div>
            <div>Lingua originale: {{element.original_language}}</div>
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
    }
  }
}
</style>