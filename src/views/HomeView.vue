<template>
  <CharactersVue />
</template>

<script>
// @ is an alias to /src
import CharactersVue from '@/components/Characters.vue';
export default {
  name: 'HomeView',
  components: {
    CharactersVue,
  },
}
</script>
