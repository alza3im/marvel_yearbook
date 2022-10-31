<template>
  <div>
    <BannerVue />

    <v-container class="my-5">

      <!-- Feature selector -->
      <v-container fluid>
        <v-row>
          <v-col class="d-flex" cols="12">
            <v-select @change="changeFeature" :items="features" label="Character Features" outlined></v-select>
          </v-col>
        </v-row>
      </v-container>

      <!-- Marvel Yearbook Collection -->
      <v-layout row wrap>
        <CharacterVue v-for="(character, index) in characters" v-bind:character="character" v-bind:index="index"
          v-bind:key="character.feature" />
      </v-layout>

    </v-container>

  </div>
</template>

<script>
import axios from 'axios'
import BannerVue from './Banner.vue';
import CharacterVue from './Character.vue';

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

      const url = `http://18.212.1.186:5000/${feature}`;
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
  components: { BannerVue, CharacterVue }
};
</script>

<style>

</style>
