<template>
  
  <div id="header">
      <div>BoolFlix</div>

      <div class="bottoneSearch">
        <input 
          type="text" 
          v-model="searchText"
          @keydown.enter.prevent="$emit('searchData', searchText)"
          >
          <!-- NOTE Utiliziamo il keydown e non il keyup perché il secondo ha problemi con il prevent -->
        <button 
          type="submit"
          @click.prevent="$emit('searchData', searchText)"
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

  .bottoneSearch{
    display: flex;
    flex-wrap: wrap;
    align-items: center;
    justify-content: space-between;
    width: fit-content;


  }

  .bottoneSearch>button{
    background-color: blue;
    color: white;
    padding: 5px;
    margin-left: 1em;
    border-radius: 10px;
  }
    
}
</style>