<template>
  <v-app>
    <v-main class="primary overflow-hidden">
      <landing/>
    </v-main>
  </v-app>
</template>

<script>
import landing from './components/landing-page';

export default {
  name: 'App',

  components: {
    landing,
  },

  data: () => ({
    //
  }),
};
</script>

