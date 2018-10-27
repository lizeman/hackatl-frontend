<template>
  <div>
    <vue-flashcard :front="frontword" :back="backword">
    </vue-flashcard>
  </div>
</template>

<script>
import vueFlashcard from 'vue-flashcard'
export default {
  data () {
    return {
      frontword: 'Opps',
      backword: 'Nope'
    }
  },
  components: {
    vueFlashcard
  },
  methods: {
    getListfromBackend () {

    }
  }
}
</script>

<style scoped>

</style>
