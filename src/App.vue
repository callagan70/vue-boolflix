<template>
<div>
  <HeaderComp  
    @searchData="metodoSearch"
  />
  <main>
          <span>Film</span>
    <div class="movie_card">

            <FilmCard
              v-for="(element, index) in filmCards"
              :key="index"
              :titolo="element.original_title"
              :titolo2="element.title"
              :lingua="element.original_language"
              :voto="element.vote_average"
          />

    </div>
      <!-- <br><br> -->
          <span>Serie tv</span>
    <div class="movie_card">

            <TvCard
            v-for="(element, index) in tvData"
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
    ApiSearch: '',
       filmData: [
{
"adult": false,
"backdrop_path": "/jA09e9RryWU4zKOTxTDKVbnFHlE.jpg",
"genre_ids": [
99
],
"id": 244214,
"original_language": "en",
"original_title": "Star Trek: Secrets of the Universe",
"overview": "Is building our own starship Enterprise possible? Will we ever travel between the stars as easily as they do in Star Trek? JJ Abrams' new feature, Star Trek Into Darkness, hits the screen in a golden age of scientific discoveries. HISTORY is there, giving viewers a deep look behind the scenes, on the set, and into the science–amazing new exoplanets, the physics of Warp drive, and the ideas behind how we might one day live in a Star Trek Universe.",
"popularity": 7.126,
"poster_path": "/yn5uWoBdjKvJA8m04z4H2sjUeRC.jpg",
"release_date": "2013-05-16",
"title": "Star Trek: Secrets of the Universe",
"video": false,
"vote_average": 6,
"vote_count": 3
},
{
"adult": false,
"backdrop_path": "/fq3wyOs1RHyz2yfzsb4sck7aWRG.jpg",
"genre_ids": [
12,
35,
878,
10751
],
"id": 105,
"original_language": "en",
"original_title": "Back to the Future",
"overview": "Eighties teenager Marty McFly is accidentally sent back in time to 1955, inadvertently disrupting his parents' first meeting and attracting his mother's romantic interest. Marty must repair the damage to history by rekindling his parents' romance and - with the help of his eccentric inventor friend Doc Brown - return to 1985.",
"popularity": 59.21,
"poster_path": "/7lyBcpYB0Qt8gYhXYaEZUNlNQAv.jpg",
"release_date": "1985-07-03",
"title": "Back to the Future",
"video": false,
"vote_average": 8.3,
"vote_count": 16438
},
{
"adult": false,
"backdrop_path": "/skQN2UMQKQnOTmwplcYMx6ZF4jS.jpg",
"genre_ids": [
12,
35,
10751,
878
],
"id": 165,
"original_language": "en",
"original_title": "Back to the Future Part II",
"overview": "Marty and Doc are at it again in this wacky sequel to the 1985 blockbuster as the time-traveling duo head to 2015 to nip some McFly family woes in the bud. But things go awry thanks to bully Biff Tannen and a pesky sports almanac. In a last-ditch attempt to set things straight, Marty finds himself bound for 1955 and face to face with his teenage parents -- again.",
"popularity": 29.538,
"poster_path": "/hQq8xZe5uLjFzSBt4LanNP7SQjl.jpg",
"release_date": "1989-11-22",
"title": "Back to the Future Part II",
"video": false,
"vote_average": 7.7,
"vote_count": 10563
},
{
"adult": false,
"backdrop_path": "/tVqweHgSOd6CBbqSxQp2NgRp6wz.jpg",
"genre_ids": [
99
],
"id": 373801,
"original_language": "en",
"original_title": "Back to the Present: The Special",
"overview": "Steven Spielberg's Back To The Future was a huge box-office hit in 1985 that ultimately led to two sequels. In 1989, in Back To The Future Part II, Michael J. Fox aka Marty Mc Fly and Christopher Lloyd aka DOC, travel into the future to October 21st 2015. At the time, the movie's crazy inventions seemed far from achievable but little did we know they would actually be so close to reality!",
"popularity": 2.248,
"poster_path": "/41A2syHG6khv7Ij0xmw5OzyRhmQ.jpg",
"release_date": "2015-10-18",
"title": "Back To the Present: The Special",
"video": false,
"vote_average": 7,
"vote_count": 8
},
{
"adult": false,
"backdrop_path": "/nh6mrOtIvD8MMC6JQIzwNDZi2G0.jpg",
"genre_ids": [
12,
35,
878
],
"id": 196,
"original_language": "en",
"original_title": "Back to the Future Part III",
"overview": "The final installment of the Back to the Future trilogy finds Marty digging the trusty DeLorean out of a mineshaft and looking for Doc in the Wild West of 1885. But when their time machine breaks down, the travelers are stranded in a land of spurs. More problems arise when Doc falls for pretty schoolteacher Clara Clayton, and Marty tangles with Buford Tannen.",
"popularity": 38.762,
"poster_path": "/crzoVQnMzIrRfHtQw0tLBirNfVg.jpg",
"release_date": "1990-05-25",
"title": "Back to the Future Part III",
"video": false,
"vote_average": 7.4,
"vote_count": 8590
}
],
    tvData: [
{
"adult": false,
"backdrop_path": "/jA09e9RryWU4zKOTxTDKVbnFHlE.jpg",
"genre_ids": [
99
],
"id": 244214,
"original_language": "en",
"original_title": "Star Trek: Secrets of the Universe",
"overview": "Is building our own starship Enterprise possible? Will we ever travel between the stars as easily as they do in Star Trek? JJ Abrams' new feature, Star Trek Into Darkness, hits the screen in a golden age of scientific discoveries. HISTORY is there, giving viewers a deep look behind the scenes, on the set, and into the science–amazing new exoplanets, the physics of Warp drive, and the ideas behind how we might one day live in a Star Trek Universe.",
"popularity": 7.126,
"poster_path": "/yn5uWoBdjKvJA8m04z4H2sjUeRC.jpg",
"release_date": "2013-05-16",
"title": "Star Trek: Secrets of the Universe",
"video": false,
"vote_average": 6,
"vote_count": 3
},
{
"adult": false,
"backdrop_path": "/fq3wyOs1RHyz2yfzsb4sck7aWRG.jpg",
"genre_ids": [
12,
35,
878,
10751
],
"id": 105,
"original_language": "en",
"original_title": "Back to the Future",
"overview": "Eighties teenager Marty McFly is accidentally sent back in time to 1955, inadvertently disrupting his parents' first meeting and attracting his mother's romantic interest. Marty must repair the damage to history by rekindling his parents' romance and - with the help of his eccentric inventor friend Doc Brown - return to 1985.",
"popularity": 59.21,
"poster_path": "/7lyBcpYB0Qt8gYhXYaEZUNlNQAv.jpg",
"release_date": "1985-07-03",
"title": "Back to the Future",
"video": false,
"vote_average": 8.3,
"vote_count": 16438
},
{
"adult": false,
"backdrop_path": "/skQN2UMQKQnOTmwplcYMx6ZF4jS.jpg",
"genre_ids": [
12,
35,
10751,
878
],
"id": 165,
"original_language": "en",
"original_title": "Back to the Future Part II",
"overview": "Marty and Doc are at it again in this wacky sequel to the 1985 blockbuster as the time-traveling duo head to 2015 to nip some McFly family woes in the bud. But things go awry thanks to bully Biff Tannen and a pesky sports almanac. In a last-ditch attempt to set things straight, Marty finds himself bound for 1955 and face to face with his teenage parents -- again.",
"popularity": 29.538,
"poster_path": "/hQq8xZe5uLjFzSBt4LanNP7SQjl.jpg",
"release_date": "1989-11-22",
"title": "Back to the Future Part II",
"video": false,
"vote_average": 7.7,
"vote_count": 10563
},
{
"adult": false,
"backdrop_path": "/tVqweHgSOd6CBbqSxQp2NgRp6wz.jpg",
"genre_ids": [
99
],
"id": 373801,
"original_language": "en",
"original_title": "Back to the Present: The Special",
"overview": "Steven Spielberg's Back To The Future was a huge box-office hit in 1985 that ultimately led to two sequels. In 1989, in Back To The Future Part II, Michael J. Fox aka Marty Mc Fly and Christopher Lloyd aka DOC, travel into the future to October 21st 2015. At the time, the movie's crazy inventions seemed far from achievable but little did we know they would actually be so close to reality!",
"popularity": 2.248,
"poster_path": "/41A2syHG6khv7Ij0xmw5OzyRhmQ.jpg",
"release_date": "2015-10-18",
"title": "Back To the Present: The Special",
"video": false,
"vote_average": 7,
"vote_count": 8
},
{
"adult": false,
"backdrop_path": "/nh6mrOtIvD8MMC6JQIzwNDZi2G0.jpg",
"genre_ids": [
12,
35,
878
],
"id": 196,
"original_language": "en",
"original_title": "Back to the Future Part III",
"overview": "The final installment of the Back to the Future trilogy finds Marty digging the trusty DeLorean out of a mineshaft and looking for Doc in the Wild West of 1885. But when their time machine breaks down, the travelers are stranded in a land of spurs. More problems arise when Doc falls for pretty schoolteacher Clara Clayton, and Marty tangles with Buford Tannen.",
"popularity": 38.762,
"poster_path": "/crzoVQnMzIrRfHtQw0tLBirNfVg.jpg",
"release_date": "1990-05-25",
"title": "Back to the Future Part III",
"video": false,
"vote_average": 7.4,
"vote_count": 8590
}
],
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
        .catch( (error) => {
          console.log( error )
        } )
 },



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