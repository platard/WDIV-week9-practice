<template>
  <div class="gallery-title">
    <h1>Pokemon Gallery</h1>
  </div>
  <Gallery :items="items" @toggle-caught="updateCaughtStatus"/>
</template>

<script>
import Gallery from './components/Gallery.vue'
import pokedex from "./utils/pokedex"

export default {
  components: {Gallery},
  data(){
    return {
      items: pokedex
    }
  },
  methods: {
    updateCaughtStatus(updatedItem) {
      this.items = this.items.map(item => item.id === updatedItem.id ? {...item, caught: !item.caught} : item)
    },
  }

}

</script>