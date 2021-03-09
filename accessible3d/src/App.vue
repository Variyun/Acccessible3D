<template>
  <v-app>
    <v-main class="primary overflow-hidden">
      <navbar/>
      <component v-bind:is="currentPage"></component>
    </v-main>
  </v-app>
</template>

<script>
import navbar from './components/navbar';
import home from './components/home';
import manual from './components/manual';
import examples from './components/examples';
import faq from './components/faq';

import {eventBus} from './main.js';

export default {
  name: 'App',

  components: {
    navbar,
    home,
    manual,
    examples,
    faq,
  },

  data: () => ({
    currentTab: "home",
  }),

  mounted () {
    eventBus.$on("change-page", page => {
      switch (page) {
        case 0:
          this.currentTab = "home";
          break;
        case 1:
          this.currentTab = "manual";
          break;
        case 2:
          this.currentTab = "examples";
          break;
        case 3:
          this.currentTab = "faq";
      }
    });
  },
  computed: {
    currentPage() {
      return this.currentTab;
    }
  },
};
</script>

