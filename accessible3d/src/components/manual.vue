<template> 
    <v-container class="pa-0 ma-0" fluid> 
        <v-parallax
          :height="$vuetify.breakpoint.smAndDown ? 500 : 300"
          width="100%"
          src="../assets/background.png"
        >
          <v-container fill-height>
            <v-row class="mx-auto">
                <v-col class="text-center">
                    <span
                        :class="[$vuetify.breakpoint.smAndDown ? 'display-3': 'display-4']"
                        class="font-weight-black"
                        data-aos="zoom-in" data-aos-duration="3000"
                        >
                        LET'S GET STARTED
                    </span>
                </v-col>
            </v-row>
            <v-row class="pa-0 ma-0"> 
               <v-col align="right" justify="right" width=100%>  
                   <span data-aos="zoom-in" data-aos-duration="3000">
                    Click here to download the text version
                   </span>
               </v-col>
            </v-row> 
          </v-container>
        </v-parallax>
        <v-row class="px-10">
            <v-col>
                <v-timeline
                    :dense="$vuetify.breakpoint.smAndDown" 
                    data-aos="fade-in" data-aos-duration="3000" data-aos-delay="500"
                >
                    <v-timeline-item
                    v-for="(item, i) in items"
                    :key="i"
                    :color="item.color"
                    :icon="item.icon"
                    fill-dot
                    >
                    <v-card
                        :color="item.color"
                        dark
                    >
                            <v-card-title class="title">
                            Lorem Ipsum Dolor
                            </v-card-title>
                            <v-card-text class="white text--primary">
                                <p>Lorem ipsum dolor sit amet, no nam oblique veritus. Commune scaevola imperdiet nec ut, sed euismod convenire principes at. Est et nobis iisque percipit, an vim zril disputando voluptatibus, vix an salutandi sententiae.</p>
                                <v-btn
                                    :color="item.color"
                                    class="mx-0"
                                    outlined
                                >
                                    Button
                                </v-btn>
                            </v-card-text>
                        </v-card>
                    </v-timeline-item>
                </v-timeline>
            </v-col>
        </v-row>
    </v-container>
</template>

<script>

export default {
  name: 'manual',

  data: () => ({
    items: [
    {
        color: 'red lighten-2',
        icon: 'mdi-star',
    },
    {
        color: 'purple darken-1',
        icon: 'mdi-book-variant',
    },
    {
        color: 'green lighten-1',
        icon: 'mdi-airballoon',
    },
    {
        color: 'indigo',
        icon: 'mdi-buffer',
    },
    ],
  }),
};

</script>