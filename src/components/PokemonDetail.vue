<template>
    <div class="pokemon-detail">
      <h2>{{ pokemon.name }}</h2>
      <p>Altura: {{ pokemon.height }}</p>
      <p>Peso: {{ pokemon.weight }}</p>
      <button @click="sharePokemon">Compartir</button>
      <button @click="$emit('close')">Cerrar</button>
    </div>
  </template>
  
  <script>
  export default {
    props: ['pokemon'],
    methods: {
      sharePokemon() {
        const attributes = `Nombre: ${this.pokemon.name}, Altura: ${this.pokemon.height}, Peso: ${this.pokemon.weight}`;
        navigator.clipboard.writeText(attributes)
          .then(() => alert('Pokémon copiado al portapapeles'))
          .catch(err => console.error('Error al copiar: ', err));
      }
    }
  };
  </script>
  
  <style>
  </style>