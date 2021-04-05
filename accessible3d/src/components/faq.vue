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
                      FAQ
                  </span>
              </v-col>
          </v-row>
        </v-container>
      </v-parallax>
    
      <v-row justify="center" class="ma-10" data-aos="zoom-in" data-aos-duration="1000">
        <v-expansion-panels accordion multiple focusable inset color="indigo lighten-4">
          <v-expansion-panel
            v-for="({q,a},i) in questions"
            :key="i"
          >
            <v-expansion-panel-header> {{q}} </v-expansion-panel-header>
            <v-expansion-panel-content> {{a}} </v-expansion-panel-content>
          </v-expansion-panel>
        </v-expansion-panels>
      </v-row>
      <v-row justify="center" class="ma-10" data-aos="zoom-in" data-aos-duration="1000">
        <span> Can't find your question? Contact us!</span>
      </v-row>
    </v-container>
</template>

<script>

export default {
  name: 'faq',

  data: () => ({
      questions: [
        {
          q: "How do I cheat on an exam and get away with it?",
          a: "You shouldn't cheat."
        },
        {
          q: "How do I get straight A's in school?",
          a: "Be smart."
        },
        {
          q: "How do I become successful in life?",
          a: "Get a small loan of 1 million dollars."
        },
        {
          q: "What is best in life?",
          a: "To crush your enemies, see them driven before you, and to hear the lamentations of their women."
        },
        {
          q: "Any questions?",
          a: "None from me."
        },
      ],
  }),
};

</script>