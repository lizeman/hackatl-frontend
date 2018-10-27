<template>
  <div>

    <!--<v-btn v-on:click="submitFile()">Submit</v-btn>-->
    <!--<vue-flashcard :front="frontword" :back="backword">-->
    <!--</vue-flashcard>-->
    <vue-flashcard v-for="(trans, i) in translate"
                   :key="i"
                   :front="trans.fontword"
                   :back="trans.backword">
    </vue-flashcard>
  </div>
</template>

<script>
import vueFlashcard from 'vue-flashcard'
// import axios from 'axios'
var something = {
    translate: [
        {
            fontword: '1', backword: '2'
        },
        {
            fontword: '3', backword: '4'
        },
        {
            fontword: '5', backword: '5'
        },
        {
            fontword: '6', backword: '7'
        }]


}
export default {
    data: () => (something),

  components: {
    vueFlashcard
  },
  methods: {
    getListfromBackend () {
      fetch("http://localhost:9000/trans?word=apple&to=ru")
          .then(res => res.json())
          .then((result) => {
            console.log(result);
          });
    }
  }
}
</script>

<style scoped>

</style>
