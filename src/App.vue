<template>
  <div id="app">    
    <h1>Pokémon Favoritos</h1>    
    <pokemon-list />  
  </div>
</template>

<script>
import PokemonList from './components/PokemonList.vue'
import './assets/styles.css'

export default {
  name: 'App',
  components: {
    PokemonList
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
