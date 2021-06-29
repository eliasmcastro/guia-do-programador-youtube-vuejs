<template>
  <div id="app">
    <div class="column is-half is-offset-one-quarter">
      <img src="./assets/logo.png" class="logo" alt="Pokémon">
      <h1 class="title is-size-3">Pokedex</h1>
      <input type="text" class="input is-rounded has-text-centered mb-6" placeholder="Buscar Pokémon" v-model="seach">
      <div v-for="(pokemon, index) in pokemonsFiltered" :key="pokemon.url">
        <Pokemon :num="index + 1" :name="pokemon.name" :url="pokemon.url"/>
      </div>
    </div>
  </div>
</template>

<script>
import axios from 'axios'
import Pokemon from './components/Pokemon.vue'

export default {
  name: 'App',
  
  components: {
    Pokemon
  },
  
  data() {
    return {
      pokemons: [],
      seach: ''
    }
  },
  
  created() {
    axios.get('https://pokeapi.co/api/v2/pokemon?limit=100&offset=0').then(res => {
      this.pokemons = res.data.results
    })
  },

  computed: {
    pokemonsFiltered() {
      if (this.seach === '') {
        return this.pokemons
      }

      return this.pokemons.filter(pokemon => pokemon.name.includes(this.seach.toLowerCase()))
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  background: #fafafa;
  text-align: center;
  color: #2c3e50;
}

.logo {
  width: 200px;
}

</style>