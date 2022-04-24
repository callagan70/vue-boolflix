<template>
  <div id="main">
    <div>
      <span>Film</span>
      <FilmCard />
    </div>

    <div>
      <span>Serie tv</span>
      <TvCard />
    </div>

  </div>
</template>

<script>
import FilmCard from './FilmCard.vue'
import TvCard from './TvCard.vue'

export default {
  name: 'MainComp',

components: {
    FilmCard,
    TvCard
  }
}
</script>

<style scoped lang="scss">
  #main{
      width: 100%;
      height: 93vh;
      background-color: grey;
      padding: 100px;
      color: white;
      font-family: Arial, Helvetica, sans-serif;
      font-size: 800;

}
</style>