<template>
  <header>
    ciao
    <FilmCard />
    <TvCard />
  </header>
</template>

<script>
import FilmCard from '../components/partial/FilmCard.vue'
import TvCard from '../components/partial/TvCard.vue'

export default {
  //Cambiare il nome con quello del componente creato
  name: 'MainComp',

components: {
    FilmCard,
    TvCard
  }
}
</script>

<style scoped lang="scss">
 /*Inserire style componente*/
</style>