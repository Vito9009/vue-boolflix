<template>
  <div>
      <header>
        <div class="logo">
          boolflix
        </div>
          <SearchFTV />
      </header>
  </div>
</template>

<script>
import SearchFTV from "./SearchFTV/SearchFTV.vue"

export default {
  name: 'Header',
  components: {
    SearchFTV
  }
}
</script>

<style lang="scss" scoped>

header{
  height: 60px;
  background-color: rgb(0, 0, 0);
  display: flex;

  .logo{
    width: 50%;
    color: rgb(255, 0, 0);
    text-transform: uppercase;
    font-weight: bold;
    display: flex;
    justify-content: start;
    align-items: center;
    padding: 20px;
  }
}
</style>