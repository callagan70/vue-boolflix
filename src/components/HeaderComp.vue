<template>
  
  <div id="header">
      <div>BoolFlix</div>
      <div>
        <input type="text" v-model="searchText">
        <button 
          type="submit"
          class="bottoneSearch"
          @click="$emit('searchData', searchText)"
        >Cerca</button>
      </div>
  </div>

</template>

<script>
export default {
  name: 'HeaderComp',

  data (){
    return {
      searchText: '',
      }},

}

// console.log(searchText)

</script>

<style scoped lang="scss">
#header{
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 0px 2em 0px 2em;
  width: 100%;
  height: 7vh;
  background: black;
  color: red;
  font-family: Arial, Helvetica, sans-serif;
  text-size-adjust: 800;
  font-size: 2em;
}
</style>