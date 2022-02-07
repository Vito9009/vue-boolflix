<template>
  <div class="container-search">
    <div class="input-container">
      <input 
      type="text" 
      placeholder="Cerca il film o la serie TV che preferisci" 
      v-model="inputText" 
      >
    </div>

    <div class="btn-container">
      <button
      type="submit"
      class="my_search-btn" 
      @click="$emit('filterX', inputText)">
      Cerca
      </button>
    </div>
  </div>
</template>

<script>

export default {
  name: 'SearchFTV',
  data() {
    return {
      inputText: ""
    }
  },
  components: {
    
  }
}
</script>

<style lang="scss" scoped>

.container-search{
  display: flex;
  justify-content: flex-end;
  align-items: center;
  height: 100%;
  width: 50%;
  padding: 20px;

  .input-container{
    padding: 10px;
    input{
      width: 300px;
      text-align: center;
      border: none;
      padding: 3px;
      border-radius: 25px;
    }
  }

  .btn-container{
    button{
      width: 50px;
      padding: 3px;
      border: none;
      border-radius: 25px;
    }
  }
}

</style>