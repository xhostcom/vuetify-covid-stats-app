<template>
 <v-app light>
  <v-toolbar fixed app light clipped-left color="primary" class="elevation-2">
    <v-toolbar-side-icon @click="drawer = !drawer"  class="white--text"></v-toolbar-side-icon>
    <v-toolbar-title class="white--text"><img src="./assets/covid.png" width="140px" /></v-toolbar-title>
  </v-toolbar>
  <v-content>
  <v-container fluid>
    <!--The MainContent Component goes here-->
  <MainContent :countries="countries"></MainContent>
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
import axios from 'axios' //import the axios a HTTP library to connect the app with the API
import MainContent from './components/MainContent.vue' // import the MainContent component
export default {
    components: {
      MainContent
  },
  data() {
    return {
      countries: [],
      errors: [],
    }
  },
   created () {
    axios.defaults.headers.common['x-rapidapi-host'] = 'covid-193.p.rapidapi.com';
    axios.defaults.headers.common['x-rapidapi-key'] = 'd6170fbf28msh711604efe0f7970p1ce9f3jsnf68590abbea1';
    axios.get('https://covid-193.p.rapidapi.com/statistics')
      .then(response => {
        let countries = response.data.response;
        console.log(countries)
        .catch(e => {
        this.errors.push(e)
      })
    })
  },
  methods: {}
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
