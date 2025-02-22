<template>
    <div>
      <div v-if="loading" class="loading">
        <img src="https://www.figma.com/design/RxextQHeFs98SQKdpTrahk/Pok%C3%A9dex?node-id=13-71&t=htbnxavjEJzKAcTs-4" alt="Cargando..." />
      </div>
      <ul class="pokemon-list">
        <li v-for="pokemon in pokemons" :key="pokemon.name" class="pokemon-item">
          <span>{{ pokemon.name }}</span>
          <button @click="getPokemonDetail(pokemon.name)">Detalles</button>
        </li>
      </ul>
      <pokemon-detail
        v-if="selectedPokemon"
        :pokemon="selectedPokemon"
        @close="selectedPokemon = null"
      />
    </div>
  </template>
  
  <script>
  import axios from 'axios';
  import PokemonDetail from './PokemonDetail.vue';
  
  export default {
    components: {
      PokemonDetail
    },
    data() {
      return {
        pokemons: [],
        loading: true,
        selectedPokemon: null
      };
    },
    mounted() {
      this.fetchPokemons();
    },
    methods: {
      async fetchPokemons() {
        try {
          const response = await axios.get('https://pokeapi.co/api/v2/pokemon');
          this.pokemons = response.data.results;
        } catch (error) {
          console.error(error);
        } finally {
          this.loading = false;
        }
      },
      async getPokemonDetail(name) {
        try {
          const response = await axios.get(`https://pokeapi.co/api/v2/pokemon/${name}`);
          this.selectedPokemon = response.data;
        } catch (error) {
          console.error(error);
        }
      }
    }
  };
  </script>
  
  <style>
  .loading {
    /* Añade aquí efectos CSS para el loading */
  }
  </style>