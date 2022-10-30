<template>
  <v-flex xs12 sm6 md4 lg3>
    <v-card color="#212124" dark flat class="text-xs-center ma-3">
      <v-responsive class="pt-4">
        <v-img :src="character.thumbnail"></v-img>
      </v-responsive>
      <v-card-text>
        <div class="white--text subheading">
          <strong>{{ character.feature }}</strong>
        </div>
      </v-card-text>
    </v-card>
  </v-flex>

</template>
<script>

export default {
  name: 'CharacterVue',
  props: ['character']
}
</script>
<style lang="css">
img {
  height: 100vh;
}
</style>
