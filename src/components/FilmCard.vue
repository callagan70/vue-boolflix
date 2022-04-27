<template>
  <div id="card">
          <h3>{{titolo}}</h3>
          <h3>{{titolo2}}</h3>
          <h4>{{lingua}}</h4>
          <h4>{{voto}}</h4>
  </div>
</template>

<script>
// import cardstyle from '../assets/style/cardstyle.scss'
export default {
  //Cambiare il nome con quello del componente creato
  name: 'FilmCard',

    props: {
    titolo: String,
    titolo2: String,
    lingua: String,
    voto: Number,
  },

  data(){
    return{
              
    }
  }

}
</script>

<style scoped lang="scss">
@import '../assets/style/cardstyle.scss'

      // #card{
      //   width: 200px;
      //   text-align: center;
      //   background: black;
      //   margin-top: 1em;
      //   margin-right: 1em;

      // }

</style>