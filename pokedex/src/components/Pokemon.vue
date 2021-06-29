<template>
  <div class="card mb-4">
    <div class="card-image">
      <figure>
        <img :src="currentImg" alt="Placeholder image" @mouseover="changeSprite">
      </figure>
    </div>
    <div class="card-content">
      <div class="media">
        <div class="media-content">
          <p class="title is-4">{{ num }} - {{ name | upper }}</p>
          <p class="subtitle is-6">{{ pokemon.type }}</p>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import axios from 'axios'

export default {
  name: 'Pokemon',
  
  props: {
    num: Number,
    name: String,
    url: String
  },

  data() {
    return {
      pokemon: {
        type: '',
        front: '',
        back: ''
      },
      isFront: true,
      currentImg: ''
    }
  },

  mounted() {
    axios.get(this.url).then(res => {
      const data = res.data

      this.pokemon.type = data.types[0].type.name
      this.pokemon.front = data.sprites.front_default
      this.pokemon.back = data.sprites.back_default

      this.currentImg = this.pokemon.front
    })
  },

  methods: {
    changeSprite() {
      if (this.isFront) {
        this.isFront = false
        this.currentImg = this.pokemon.back
      } else {
        this.isFront = true
        this.currentImg = this.pokemon.front
      }
    }
  },

  filters: {
    upper(value) {
      return value[0].toUpperCase() + value.slice(1)
    }
  }
}
</script>

<style scoped>
  img {
    cursor: pointer;
    opacity: 0.8;
  }
</style>