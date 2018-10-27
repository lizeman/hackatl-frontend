<template>
  <v-app>
    <v-toolbar app>
      <v-toolbar-title class="headline text-uppercase">
        <span>Vuetify</span>
        <span class="font-weight-light">MATERIAL DESIGN</span>
      </v-toolbar-title>
      <v-spacer></v-spacer>
      <v-btn
        flat
        href="https://github.com/vuetifyjs/vuetify/releases/latest"
        target="_blank"
      >
        <span class="mr-2">Latest Release</span>
      </v-btn>
    </v-toolbar>

    <v-content>
      <upload/>
    </v-content>


    <v-content>
      <Flashcard/>
    </v-content>

    <!--<v-content>-->
      <!--<HelloWorld/>-->
    <!--</v-content>-->


  </v-app>
</template>

<script>
import Flashcard from './components/Flashcard'
import Upload from './components/upload'
export default {
  name: 'App',
  components: {
      Flashcard,
      Upload,
  },
  data () {
    return {
      //
    }
  }
}
</script>
