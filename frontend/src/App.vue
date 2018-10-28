<template>
  <v-app>
    <v-toolbar app>
      <v-toolbar-title class="headline text-uppercase">
        <span>Future Flash Card</span>
        <span class="font-weight-light">Automated Generated Flashcard</span>
      </v-toolbar-title>
      <v-spacer></v-spacer>
      <!--<v-btn-->
        <!--flat-->
        <!--href="https://github.com/vuetifyjs/vuetify/releases/latest"-->
        <!--target="_blank"-->
      <!--&gt;-->
        <!--<span class="mr-2">Latest Release</span>-->
      <!--</v-btn>-->
    </v-toolbar>

    <!--<v-content>-->
      <!--<upload/>-->
    <!--</v-content>-->

    <v-content>
      <uploadtwo/>
    </v-content>

    <v-content>
      <language/>
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
import uploadtwo from './components/uploadtwo'
import language from'./components/language'
export default {
  name: 'App',
  components: {
      Flashcard,
      language,
      uploadtwo,
  },
  data () {
    return {
      //
    }
  }
}
</script>
