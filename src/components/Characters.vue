<template>
  <div>
    <BannerVue />

    <v-container class="my-5">

      <!-- Marvel Yearbook Collection -->
      <v-layout row wrap>
      </v-layout>

    </v-container>

  </div>
</template>

<script>
import axios from 'axios'
import BannerVue from './Banner.vue';

export default {
  name: 'CharactersVue',
  data() {
    return {
      characters: [],
      thumbnailSize: 'standard_fantastic.jpg',  // From the documentation
      features: ['name', 'stories', 'comics', 'series'],
      featureMap: { 'name': 'name', 'stories': 'title', 'comics': 'title', 'series': 'title' }

    };
  },
  methods: {
    getFeatureName: function (feature) {
      return this.featureMap[feature];
    },
    changeFeature(feature) {

      const url = `http://0.0.0.0:5000/${feature}`;
      let attribute = this.getFeatureName(feature);
      axios.get(url)
        .then((result) => {
          this.characters = []
          result.data.forEach(element => {
            let thumbnail = (`${element.thumbnail.path}/${this.thumbnailSize}`)
            element['thumbnail'] = thumbnail
            element['feature'] = element[attribute]
            this.characters.push(element);
          });
        }).catch((error) => {
          alert(error);
        });

    }
  },
  components: { BannerVue }
};
</script>

<style>

</style>
