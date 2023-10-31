<template>
    <div id="gallery" class="gallery">
        <div v-for="item in items" :key="item.id" 
        :class="item.caught ? 'gallery-item caught' : 'gallery-item'"
        @click="toggleCaught(item)" >
            <img class="gallery-item-image" :src=" `https://raw.githubusercontent.com/PokeAPI/sprites/master/sprites/pokemon/${item.id}.png` " />
            <h2 class="gallery-item-name"> {{ item.name }} </h2>
        </div>
  
    </div>
</template>

<script>

export default {
    props:['items'],
    methods: {
        toggleCaught(item) {
            this.$emit('toggle-caught', item)
        }
    }
}

</script>

<style>
    .caught{
        background-color: gainsboro;
    }

</style>