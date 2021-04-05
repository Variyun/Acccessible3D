<template> 
    <v-container class="pa-0 ma-0" fluid> 
      <v-img
          :max-height="'calc(90vh)'"
          src="../assets/background.png"
      >
        <v-container fill-height>
          <v-row class="text-center" justify="center">
            <h2 class="display-2 font-weight-bold" data-aos="zoom-in" data-aos-duration="800">TRY CREATING MODELS WITH OUR DATASETS</h2>
            <v-col
              data-aos="fade-up" data-aos-duration="1000" data-aos-delay="500"
              v-for="({title, image, download}, i) in projects"
              :key="i"
              cols="12"
              md="4"
            >
              <v-hover v-slot="{ hover }">
                <v-card
                  class="pa-0 black--text"
                  color="grey lighten-3"
                  flat
                >
                  <v-img
                    :aspect-ratio="4/5"
                    :src="image"
                  >
                    <v-fade-transition>
                      <div
                        v-if="hover"
                        class="d-flex transition-fast-in-fast-out black v-card--reveal display-3 white--text"
                        style="height: 100%;"
                      >
                        <v-tooltip bottom>
                          <template v-slot:activator="{ on, attrs }">
                            <v-btn icon x-large v-bind="attrs" v-on="on"> 
                              <v-icon>mdi-download</v-icon>
                            </v-btn>
                          </template>
                          <span> Download dataset</span>
                        </v-tooltip>
                      </div>
                    </v-fade-transition>
                  </v-img>
                  <v-bottom-navigation>
                    <v-btn block disabled><span class="text-uppercase"> {{ title }}</span></v-btn>
                  </v-bottom-navigation>
                </v-card>
              </v-hover>
            </v-col>
          </v-row>
        </v-container>
      </v-img>
    </v-container>
</template>

<style scoped>
  .v-card--reveal {
    align-items: center;
    bottom: 0;
    justify-content: center;
    opacity: .8;
    position: absolute;
    width: 100%;
  }
</style>


<script>
export default {
  name: 'examples',

  data: () => ({
    projects: [
        {
          title: 'Statue',
          image: 'https://i.imgur.com/KKQQNpQ.png',
          download: 'Lorem ipsum dolor sit amet consectetur adipisicing elit. Iusto cupiditate sint possimus quidem atque harum excepturi nemo velit tempora! Enim inventore fuga, qui ipsum eveniet facilis obcaecati corrupti asperiores nam',
        },
        {
          title: 'Stack of Books',
          image: 'https://i.imgur.com/Fw2yJ2j.png',
          download: 'Sed ut elementum justo. Suspendisse non justo enim. Vestibulum cursus mauris dui, a luctus ex blandit. Lorem ipsum dolor sit amet consectetur adipisicing elit. qui ipsum eveniet facilis obcaecati corrupti consectetur adipisicing elit.',
        },
        {
          title: 'Totem of Bad Luck',
          image: 'https://i.imgur.com/9Oivncr.png',
          download: 'Lorem ipsum dolor sit amet consectetur adipisicing elit. Iusto cupiditate sint possimus quidem atque harum excepturi nemo velit tempora! Enim inventore fuga, qui ipsum eveniet facilis obcaecati corrupti asperiores nam',
        },
      ],
  }),
};

</script>