<template>
    <file-upload :url='url' :thumb-url='thumbUrl' :headers="headers" @change="onFileChange"></file-upload>
</template>

<script>
    import Vue from 'vue'
    import FileUpload from 'v-file-upload'
    Vue.use(FileUpload)

    export default {
        data () {
            return {
                url: 'http://128.61.45.90:8080/detector',
                // headers: {'access-token': '<your-token>'},
                filesUploaded: []
            }
        },
        methods: {
            thumbUrl (file) {
                return file.myThumbUrlProperty
            },
            onFileChange (file) {
                // Handle files like:
                this.fileUploaded = file
            }
        }
    }
</script>

<style scoped>

</style>
