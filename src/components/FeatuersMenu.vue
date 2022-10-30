<template>
  <v-container fluid>
    <v-row align="center">
      <v-col class="d-flex" cols="12">
        <v-select :items="features" label="Character Features" outlined></v-select>
      </v-col>

    </v-row>
  </v-container>
</template>
<script>
export default {
  name: 'FeaturesMenuVue',
  data() {
    return {
      features: ['name', 'stories', 'comics', 'series'],
    }
  }
}
</script>
