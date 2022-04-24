<template>
  <div>
    <FilmCard />
    <TvCard />
  </div>
</template>

<script>
import FilmCard from '../components/partial/FilmCard.vue'
import TvCard from '../components/partial/TvCard.vue'

export default {
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