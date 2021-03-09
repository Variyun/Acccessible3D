<template> 
    <v-container class="pa-0 ma-0" fluid> 
            <v-app-bar
            app
            dark
            height="50%"
            >
            <v-icon x-large>mdi-video-3d</v-icon>
            <v-tabs 
                right 
                show-arrows
                color="indigo lighten-4"
                v-model="tab"
            > 
                <v-tab>HOME</v-tab>
                <v-tab>GET STARTED</v-tab>
                <v-tab>EXAMPLES</v-tab>
                <v-tab>FAQ</v-tab>
            </v-tabs>
            
            </v-app-bar>
    </v-container>
</template>

<script>
import {eventBus} from '../main.js';

export default {
  name: 'navbar',

  data: () => ({
      tab: 0,
  }),
  
  watch: {
      tab: function() {
          eventBus.$emit("change-page", this.tab);
      }
  },
};
</script>