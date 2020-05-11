<template>
 <v-app light>
  <v-toolbar fixed app light clipped-left color="primary" class="elevation-2">
    <v-toolbar-side-icon @click="drawer = !drawer"  class="white--text"></v-toolbar-side-icon>
    <v-toolbar-title class="white--text"><img src="./assets/covid.png" width="140px" /></v-toolbar-title>
  </v-toolbar>
  <v-content>
  <v-container fluid>
    <v-layout row wrap align-center>
      <v-flex xs12>
            <div v-for="index in countries" :key="index">
              <v-card hover data-aos="zoom-in" data-aos-easing="ease">
                  <v-container fill-height fluid>
                    <v-layout>
                      <v-flex xs12 align-end d-flex>
                        <span class="headline">{{ countries.country }}</span>
                      </v-flex>
                    </v-layout>
                  </v-container>
                <v-card-text>
                  <h3>Country</h3>
                </v-card-text>
                <v-card-actions>
                 <v-chip small color="secondary" class="white--text">
                  <h4>Country</h4>
                </v-chip>
                <v-spacer></v-spacer>
                <v-btn icon class="red--text">
                <v-icon small>fa-reddit</v-icon>
                </v-btn>
                <v-btn icon class="light-blue--text">
                  <v-icon small>fa-twitter</v-icon>
                </v-btn>
                <v-btn icon class="blue--text text--darken-4">
                  <v-icon small>fa-facebook</v-icon>
                </v-btn>
                <v-btn icon class="red--text">
                  <v-icon small>fa-google-plus</v-icon>
                </v-btn>
                <v-btn icon class="blue--text text--darken-4">
                  <v-icon small>fa-linkedin</v-icon>
                </v-btn>
                <v-spacer></v-spacer>
              </v-card-actions>
            </v-card>
            </div>
          </v-flex>
       </v-layout>
     </v-container>
   </v-content>
   <v-footer class="secondary" app>
      <v-layout row wrap align-center>
        <v-flex xs12>
          <div class="white--text ml-3">
            Made with
            <v-icon class="red--text">heart</v-icon>
            by <a class="white--text" href="https://vuetifyjs.com" target="_blank">Vuetify</a>
            and <a class="white--text" href="https://github.com/xhostcom" target="_blank">Paul Anthony McGowan</a>
          </div>
        </v-flex>
      </v-layout>
    </v-footer>
  </v-app>
</template>
<script>
import axios from 'axios';
export default {
  data() {
    return {
      countries: [
        {
        country: '',
        cases: {
          new: '',
          active: '',
          critical: '',
          recovered: '',
          total: ''
        },
        deaths: {
          total: ''
       }
       }
      ]
    }
   },
   created () {
    axios.defaults.headers.common['x-rapidapi-host'] = 'covid-193.p.rapidapi.com';
    axios.defaults.headers.common['x-rapidapi-key'] = 'd6170fbf28msh711604efe0f7970p1ce9f3jsnf68590abbea1';
    axios.get('https://covid-193.p.rapidapi.com/statistics')
      .then(response => {
        let countries = response.data.response;
        console.log(countries)

    })
   }
  }
</script>
<style scoped>
#app > div > nav > div > div > img {
margin-top: 6px;
}
.secondary {
background: rgb(3, 24, 56)!important;
}
</style>
