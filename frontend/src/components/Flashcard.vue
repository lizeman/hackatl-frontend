<template>
  <div>

    <!--<v-btn v-on:click="submitFile()">Submit</v-btn>-->
    <!--<vue-flashcard :front="frontword" :back="backword">-->
    <!--</vue-flashcard>-->
    <vue-flashcard v-for="(trans, i) in translate"
                   :key="i"
                   :front="trans.name"
                   :back="trans.translation"
                   :img-back="trans.link"
                   :img-front="trans.link"
    >
    </vue-flashcard>
  </div>
</template>

<script>
import vueFlashcard from 'vue-flashcard'
import axios from 'axios'
// var something = {
//     translate: [
//         {
//             name: '1', translation: '2', link: 'https://vuejs.org/images/logo.png'
//         },
//         ]
// }
var something = {
    translate: [
        ]
}


axios.get("http://128.61.45.90:8080/Cards/all")
    .then(response => {
        console.log(response.data)
        for (var i = 0; i < response.data.length; i++)
            something.translate.push(response.data[i])
    })


export default {
    data: () => (something),

  components: {
    vueFlashcard
  },
  methods: {

  }
}
</script>

<style scoped>

</style>
