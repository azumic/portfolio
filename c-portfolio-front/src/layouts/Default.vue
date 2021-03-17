<template>
  <v-app>



      <v-parallax
        dark
        src="https://i.imgur.com/JqbRgSK.gif"
      >
        <v-row
          align="center"
          justify="center"
        >
          <v-col
            class="text-center"
            cols="12"
          >
            <h1 class="display-1 font-weight-thin mb-4">
              Welcome
            </h1>
            
            <div>
            <small class="subheading font-weight-thin p-3"/>
            </div>
            <v-btn
                v-for="icon in icons"
                :key="icon"
                class="mx-4 white--text mt-5"
                icon
              >
                <v-icon size="24px">
                  {{ icon }}
                </v-icon>
              </v-btn> 
          </v-col>
        </v-row>
      </v-parallax>





        <v-main v-if="tab == 0">
        <slot/>
        </v-main>

        <About v-if="tab == 1"/>

      
        <v-footer
          dark
          padless
          class="mt-3"
        >
          <v-card
            flat
            tile
            class="indigo lighten-1 white--text text-center"
          >
            <v-card-text>
              <v-btn
                v-for="icon in icons"
                :key="icon"
                class="mx-4 white--text"
                icon
              >
                <v-icon size="24px">
                  {{ icon }}
                </v-icon>
              </v-btn>
            </v-card-text>

            <v-card-text class="white--text pt-0">
              Phasellus feugiat arcu sapien, et iaculis ipsum elementum sit amet. Mauris cursus commodo interdum. Praesent ut risus eget metus luctus accumsan id ultrices nunc. Sed at orci sed massa consectetur dignissim a sit amet dui. Duis commodo vitae velit et faucibus. Morbi vehicula lacinia malesuada. Nulla placerat augue vel ipsum ultrices, cursus iaculis dui sollicitudin. Vestibulum eu ipsum vel diam elementum tempor vel ut orci. Orci varius natoque penatibus et magnis dis parturient montes, nascetur ridiculus mus.
            </v-card-text>

            <v-divider></v-divider>

            <v-card-text class="white--text">
              {{ new Date().getFullYear() }} — <strong>Vuetify</strong>
            </v-card-text>
          </v-card>
        </v-footer>

        <v-bottom-navigation
          :value="value"
          horizontal
          app
        >


          <v-btn v-on:click="tab = 1">
            <span>About</span>

            <v-icon>mdi-school</v-icon>
          </v-btn>

          <v-btn v-on:click="tab = 0">
            <span>Home</span>

            <v-icon>mdi-home</v-icon>
          </v-btn>
          
          <v-btn v-on:click="tab = 2">
            <span>Hire me</span>

            <v-icon>mdi-star</v-icon>
          </v-btn>

        </v-bottom-navigation>
  </v-app>
</template>

<static-query>
query {
  metadata {
    siteName
  }
}
</static-query>


<script>
import baffle from 'baffle';
import Typed from 'typed.js';
import About from '~/components/about'
  export default {
    data: () => ({
      icons: [
        'mdi-facebook',
        'mdi-twitter',
        'mdi-linkedin',
        'mdi-instagram',
      ],
      value: 1,
      tab: 0
    }),
    methods:{
      text_reveal : function (){
        let b = baffle('.display-1', {
            characters: '*@&#!)@!#1234abcdEF',
            speed: 200
        });

      b.reveal(1000);
      },
      typed : function (){

        var options = {
          strings: ['<b>Hi</b> i am Cedric', 'I am a <b>web developer</b>'],
          typeSpeed: 90,
          loop: true
        };

        var typed = new Typed('.subheading', options);

      }
    },
    components: {
      About
    },
    mounted(){
      this.text_reveal();
      this.typed();
    }
  }
</script>