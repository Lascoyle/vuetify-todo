<template>
  <v-app class="grey lighten-4">
    <navigation></navigation>
    <v-main class="mx-4 mb-4">
      <router-view></router-view>
    </v-main>

  </v-app>
</template>

<script>
import Navigation from './components/Navigation.vue';

export default {
  name: 'App',

  components: {
    'navigation': Navigation
  },

  data: () => ({
    //
  }),
};
</script>
