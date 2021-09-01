<template>
  <div class="content">
    <h1>
        Welcome to the <span>Villains</span> Page!
    </h1>
    <carousel class="carousel" :per-page="4" :mouse-drag="true" :spacePaddingMaxOffsetFactor="8" :paginationActiveColor="'#efed14'" >
    <slide v-for="villain in this.villains" :key="villain.slug">
      <villains-card :url="villain.images.lg" :name="villain.name" :description="getDescription(villain)"/>
    </slide>
  </carousel>
  </div>
</template>

<script>

import axios from 'axios';
import VillainsCard from './VillainsCard.vue';
import { Carousel, Slide } from 'vue-carousel';

export default {
  name: 'VillainsPage',
  components: {
    Carousel,
    Slide,
    VillainsCard
  },
  data: () => ({
    villains: []
  }),
  mounted() {
    this.getAllCharacters()
  },
  methods: {
    getAllCharacters() {
      axios.get('https://cdn.jsdelivr.net/gh/akabab/superhero-api@0.3.0/api/all.json')
      .then(response => (this.villains = response.data.filter(villain => villain.biography.alignment === 'bad')))
    },
    getDescription(villain){
      return `
        Full name: ${villain.biography.fullName !== "" ? villain.biography.fullName : villain.name} \n
        Race: ${villain.appearance.race ?? 'Unknown'} \n
        Publisher: ${villain.biography.publisher}
      `
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  h1 {
    font-size: 50px;
    margin: 0 30px;
    color: #FFFFFF
  }
  span {
    color: #efed14;
  }
  .content {
    height: 100%;
    background-color: #011e2c;
    padding-top: 20px;
  }
  .carousel {
    margin-top: 40px;
    margin-left: 40px;
  }
</style>
