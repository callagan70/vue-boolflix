<template>
<div>
  <HeaderComp  
    @searchData="metodoSearch"
  />
  <main>
          <span>Film</span>
    <div class="movie_card">

            <FilmCard
              v-for="(element, index) in filterMovies()"
              :key="index"
              :titolo="element.original_title"
              :titolo2="element.title"
              :lingua="element.original_language"
              :voto="element.vote_average"
          />

    </div>
      <br><br>
          <span>Serie tv</span>
    <div class="movie_card">

            <TvCard
            v-for="(element, index) in filterTv()"
            v-bind:key="index"
              :titolo="element.name"
              :titolo2="element.original_name"
              :lingua="element.original_language"
              :voto="element.vote_average"
              />
    </div>

  </main>

</div>

<!-- NOTE per le carte 3D https://www.w3schools.com/howto/howto_css_flip_card.asp -->
</template>

<script>
import HeaderComp from './components/HeaderComp.vue'
import FilmCard from './components/FilmCard.vue'
import TvCard from './components/TvCard.vue'
import axios from 'axios'

export default {
  components: {
    HeaderComp,
    TvCard,
    FilmCard
   },


  data(){
    return{
    TxtSearch: '',
    ApiKey: '6eadd5a081c4535630e8571051049891',
    filmCards: [],
    TvCards:[],
  }
},

created(){
  axios.get( 'https://api.themoviedb.org/3/search/movie?api_key=6eadd5a081c4535630e8571051049891&language=en&query=Star&page=1' )
        .then( ( res )=>{
          this.filmCards = res.data.results
            console.log(this.filmCards );
            console.log(this.filmCards[2].original_title)
         //  this.Cards = false
        } )

   axios.get( 'https://api.themoviedb.org/3/search/tv?api_key=6eadd5a081c4535630e8571051049891&language=en&query=Star&page=1' )
        .then( ( res )=>{
          this.TvCards = res.data.results
            console.log(this.TvCards );
            console.log(this.TvCards[2].name)
         //  this.Cards = false
        } )
        .catch( (error) => {
          console.log( error )
        } )
 },

methods:{
 metodoSearch(testo){
   this.TxtSearch = testo
  },

  filterMovies(){
  if (this.TxtSearch === " " ) {
    console.log(this.TxtSearch)
    return this.filmCards;
  }
    else{
        return this.filmCards.filter( (elem) => {
          return elem.original_title.toLowerCase().includes(this.TxtSearch.toLowerCase())
        } )
      }

    },

  filterTv(){
  if (this.TxtSearch === " " ) {
    console.log(this.TxtSearch)
    return this.filmCards;
  }
    else{
        return this.TvCards.filter( (elem) => {
          return elem.name.toLowerCase().includes(this.TxtSearch.toLowerCase())
        } )
      }

    }

 },

// Computed: {

// metodoSearch(){
//   if (this.TxtSearch === " " ) {
//     // mostra lista completa
//     return this.filmCards;
//   }

//     return this.filmCards.filter((item) => {
//     // il .filter crea un array con gli elementi che vengono verificati
//       return item.original_title
//         .toLowCase()
//         .includes(this.filmCards.toLowCase());
//     });
//   },
// }



// !SECTION Fine Export default
}
</script>






<style lang="scss">

*{padding: 0;
margin: 0;
box-sizing: border-box}

main{
      width: 100%;
      height: 100%;
      background-color: grey;
      padding: 100px;
      color: white;
      font-family: Arial, Helvetica, sans-serif;
      font-size: 800;
}

main>span{
  color: red;
  font-size: 2em;
}

.movie_card{
  display: flex;
  flex-wrap: wrap;
  justify-content: flex-start;
  margin-top: 1em;
  margin-bottom: 1em;
}

</style>