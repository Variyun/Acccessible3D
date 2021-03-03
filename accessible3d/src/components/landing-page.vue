<template>
  <v-container height="100%" class="pa-0 ma-0" fluid>
    <v-parallax id="back" src='../assets/background.png' height="1200">
        <v-row class="text-right ma-0 pd-0"> <v-col> <p> READY TO GET STARTED? CLICK HERE </p> </v-col> </v-row> 
        <v-row  align="center" justify="center" style="margin-bottom: 30%;" >
            <v-col class="text-center">
                <h1 class="display-4 font-weight-bold mb-5" data-aos="zoom-in" data-aos-duration="2000">
                ACCESSIBLE 3D
                </h1>
                <p class="display-1 font-weight-bold" data-aos="fade-up" data-aos-duration="2000" data-aos-delay="800">
                Reconstruct Your World
                </p>
            </v-col>
        </v-row>
    </v-parallax>

    <v-row class="pt-5" style="margin-left: 5%; margin-bottom: 15%"> 
      <v-col class="px-0 mx-0">
        <h1 class="display-2 font-weight-bold mb-5" data-aos="fade-right" data-aos-duration="1800">
          LOREM IPSUM
        </h1>
        <h2 class="font-weight-bold" style="margin-right: 10%" data-aos="fade-right" data-aos-duration="1800">
          Lorem ipsum dolor sit amet, consectetur adipiscing elit. Sed lobortis erat purus, nec dictum mi molestie accumsan. Vestibulum convallis nunc erat, eget scelerisque tortor elementum quis. Maecenas semper lacus massa, nec molestie felis faucibus elementum. Mauris libero ex, commodo at est vitae, efficitur vehicula diam. Aliquam lacus velit, dignissim nec enim in, dictum gravida est. Suspendisse et ligula ac leo volutpat elementum. Fusce a odio metus. Maecenas volutpat, erat ac porttitor hendrerit, risus nibh efficitur augue, eu fermentum dui nisi sit amet lorem. Ut convallis metus vel ex sodales, sit amet mollis eros varius. Sed malesuada nisi sit amet finibus varius.
        </h2>
      </v-col>
      <v-col align="center" justify="center">
        <v-img src="../assets/phone_white.png" 
          max-width="50%" max-height="100%" 
          class="pb-5" 
          data-aos="fade-left"
          data-aos-duration="2000"> 
        </v-img>
      </v-col> 
    </v-row>

    <v-row style="margin-left: 5%;">
     <v-col class="px-0 mx-0">
        <h1 class="display-2 font-weight-bold mb-5"  data-aos="fade-up" data-aos-duration="1800">
          LOREM IPSUM
        </h1>
        <h2 class="font-weight-bold" style="margin-right: 10%"  data-aos="fade-up" data-aos-duration="1800">
          Lorem ipsum dolor sit amet, consectetur adipiscing elit. Sed lobortis erat purus, nec dictum mi molestie accumsan. Vestibulum convallis nunc erat, eget scelerisque tortor elementum quis. Maecenas semper lacus massa, nec molestie felis faucibus elementum. Mauris libero ex, commodo at est vitae, efficitur vehicula diam. Aliquam lacus velit, dignissim nec enim in, dictum gravida est. Suspendisse et ligula ac leo volutpat elementum. Fusce a odio metus. Maecenas volutpat, erat ac porttitor hendrerit, risus nibh efficitur augue, eu fermentum dui nisi sit amet lorem. Ut convallis metus vel ex sodales, sit amet mollis eros varius. Sed malesuada nisi sit amet finibus varius.
        </h2>
      </v-col>
    </v-row> 
    <v-fab-transition>
      <v-btn
        v-scroll="onScroll"
        v-show="fab"
        elevation="0"
        large
        fab
        fixed
        bottom
        right
        color="primary"
        @click="toTop"
      >
        <v-icon>mdi-arrow-up</v-icon>
      </v-btn>
    </v-fab-transition>
  </v-container>
</template>

<script>
  //Animation Library
  import AOS from 'aos';
  import 'aos/dist/aos.css';
  AOS.init();

  export default {
    name: 'landing',
    methods: {
      onScroll (e) {
        if (typeof window === 'undefined') return
        const top = window.pageYOffset ||   e.target.scrollTop || 0
        this.fab = top > 20
      },
      toTop () {
        this.$vuetify.goTo(0)
      }
    },
    data: () => ({
    fab:false
    }),
  }
</script>
