<template>
<div>
  <HeaderComp />
  <MainComp />
</div>
</template>

<script>
 import HeaderComp from './components/HeaderComp.vue'
 import MainComp from './components/MainComp.vue'

export default {
  components: {
     HeaderComp,
     MainComp,
   },

  data(){
    return{
    TxtSearch: '' 
  }},

    // methods: {
    //     metodoSearch( testo ){
    //   this.TxtSearch = testo
    //     console.log(testo)
    //   }
    // },
 }
</script>

<style lang="scss">
*{padding: 0;
margin: 0;
box-sizing: border-box}
</style>



// <script>
