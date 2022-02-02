<template>
  <div class="container-search">
    <div class="input-container">
      <input 
      type="text" 
      placeholder="Cerca il fil o la serie TV che preferisci" 
      v-model="inputText">
    </div>

    <div class="btn-container">
      <button
      type="submit"
      class="my_search-btn"
      >
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
  justify-content: end;
  align-items: center;
  height: 100%;
  width: 50%;
  padding: 20px;

  .input-container{
    padding: 10px;
    input{
      width: 300px;
      text-align: center;
    }
  }
}

</style>