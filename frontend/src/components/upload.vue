<template>
    <div class="container">
        <div class="large-12 medium-12 small-12 cell">
            <label>File
                <input type="file" id="file" ref="file" v-on:change="handleFileUpload()"/>
            </label>
            <v-btn v-on:click="submitFile()">Submit</v-btn>
        </div>
    </div>
</template>

<script>
    import axios from 'axios'
    export default {
        /*
          Defines the data used by the component
        */
        data(){
            return {
                file: ''
            }
        },

        methods: {
            /*
              Submits the file to the server
            */
            submitFile(){
                /*
                        Initialize the form data
                    */
                let formData = new FormData();

                /*
                    Add the form data we need to submit
                */
                formData.append('file', this.file);

                fetch('http://localhost:9000/fileUpload', {
                    method: 'POST',
                    headers: {'Content-Type':'multipart/form-data'},
                    body: {formData}
                })
                .then((response) => response.json())
                        .then((data)=>{
                            this.setState({images: data.images, isLoading: false});
                            this.props.updateImages(data.images);
                        })
                        .catch(error => this.setState({ error, isLoading: false}));

                /*
                  Make the request to the POST /single-file URL
                */
                /*axios.post( 'http://localhost:9000/fileUpload',
                    formData,
                    {
                        headers: {
                            'Content-Type': 'multipart/form-data'
                        }
                    }
                ).then(function(){
                })
                    .catch(function(){
                    });*/
            },

            /*
              Handles a change on the file upload
            */
            handleFileUpload(){
                this.file = this.$refs.file.files[0];
            }
        }
    }
</script>


<!--&lt;!&ndash;<template>&ndash;&gt;-->
    <!--&lt;!&ndash;<div>&ndash;&gt;-->
        <!--&lt;!&ndash;<v-app>&ndash;&gt;-->
            <!--&lt;!&ndash;<v-content>&ndash;&gt;-->
                <!--&lt;!&ndash;<v-container fluid>&ndash;&gt;-->
                    <!--&lt;!&ndash;<img :src="imageUrl" height="150" v-if="imageUrl"/>&ndash;&gt;-->
                    <!--&lt;!&ndash;<v-text-field label="Select Image" @click='pickFile' v-model='imageName' prepend-icon='attach_file'></v-text-field>&ndash;&gt;-->
                    <!--&lt;!&ndash;<input&ndash;&gt;-->
                            <!--&lt;!&ndash;type="file"&ndash;&gt;-->
                            <!--&lt;!&ndash;style="display: none"&ndash;&gt;-->
                            <!--&lt;!&ndash;ref="image"&ndash;&gt;-->
                            <!--&lt;!&ndash;accept="image/*"&ndash;&gt;-->
                            <!--&lt;!&ndash;@change="onFilePicked"&ndash;&gt;-->
                    <!--&lt;!&ndash;&gt;&ndash;&gt;-->
                <!--&lt;!&ndash;</v-container>&ndash;&gt;-->
            <!--&lt;!&ndash;</v-content>&ndash;&gt;-->
        <!--&lt;!&ndash;</v-app>&ndash;&gt;-->
    <!--&lt;!&ndash;</div>&ndash;&gt;-->
<!--&lt;!&ndash;</template>&ndash;&gt;-->

<!--&lt;!&ndash;<script>&ndash;&gt;-->
    <!--&lt;!&ndash;export default {&ndash;&gt;-->
        <!--&lt;!&ndash;el: '#app',&ndash;&gt;-->
            <!--&lt;!&ndash;data: () => ({&ndash;&gt;-->
        <!--&lt;!&ndash;title: "Image Upload",&ndash;&gt;-->
        <!--&lt;!&ndash;dialog: false,&ndash;&gt;-->
        <!--&lt;!&ndash;imageName: '',&ndash;&gt;-->
        <!--&lt;!&ndash;imageUrl: '',&ndash;&gt;-->
        <!--&lt;!&ndash;imageFile: ''&ndash;&gt;-->
    <!--&lt;!&ndash;}),&ndash;&gt;-->

        <!--&lt;!&ndash;methods: {&ndash;&gt;-->
        <!--&lt;!&ndash;pickFile () {&ndash;&gt;-->
            <!--&lt;!&ndash;this.$refs.image.click ()&ndash;&gt;-->
        <!--&lt;!&ndash;},&ndash;&gt;-->

        <!--&lt;!&ndash;onFilePicked (e) {&ndash;&gt;-->
            <!--&lt;!&ndash;const files = e.target.files&ndash;&gt;-->
            <!--&lt;!&ndash;if(files[0] !== undefined) {&ndash;&gt;-->
                <!--&lt;!&ndash;this.imageName = files[0].name&ndash;&gt;-->
                <!--&lt;!&ndash;if(this.imageName.lastIndexOf('.') <= 0) {&ndash;&gt;-->
                    <!--&lt;!&ndash;return&ndash;&gt;-->
                <!--&lt;!&ndash;}&ndash;&gt;-->
                <!--&lt;!&ndash;const fr = new FileReader ()&ndash;&gt;-->
                <!--&lt;!&ndash;fr.readAsDataURL(files[0])&ndash;&gt;-->
                <!--&lt;!&ndash;fr.addEventListener('load', () => {&ndash;&gt;-->
                    <!--&lt;!&ndash;this.imageUrl = fr.result&ndash;&gt;-->
                    <!--&lt;!&ndash;this.imageFile = files[0] // this is an image file that can be sent to server...&ndash;&gt;-->
                <!--&lt;!&ndash;})&ndash;&gt;-->
            <!--&lt;!&ndash;} else {&ndash;&gt;-->
                <!--&lt;!&ndash;this.imageName = ''&ndash;&gt;-->
                <!--&lt;!&ndash;this.imageFile = ''&ndash;&gt;-->
                <!--&lt;!&ndash;this.imageUrl = ''&ndash;&gt;-->
            <!--&lt;!&ndash;}&ndash;&gt;-->
        <!--&lt;!&ndash;}&ndash;&gt;-->
    <!--&lt;!&ndash;}&ndash;&gt;-->

    <!--&lt;!&ndash;}&ndash;&gt;-->
<!--&lt;!&ndash;</script>&ndash;&gt;-->

<!--&lt;!&ndash;<style scoped>&ndash;&gt;-->

<!--&lt;!&ndash;</style>&ndash;&gt;-->


<!--<template>-->
    <!--<div class="btn btn-primary jbtn-file"> {{ title }}<input-->
            <!--type="file" v-on:change="fileSelected">-->

    <!--</div>-->
<!--</template>-->

<!--<script>-->
    <!--export default {-->
        <!--name: 'upload-button',-->
        <!--props: {-->
            <!--selectedCallback: Function,-->
            <!--title: String-->
        <!--},-->
        <!--methods: {-->
            <!--fileSelected(e) {-->
                <!--if (this.selectedCallback) {-->
                    <!--if (e.target.files[0]) {-->
                        <!--this.selectedCallback(e.target.files[0]);-->
                    <!--} else {-->
                        <!--this.selectedCallback(null);-->
                    <!--}-->
                <!--}-->
            <!--}-->
        <!--}-->
    <!--}-->
<!--</script>-->

<!--<style scoped>-->
    <!--.jbtn-file {-->
        <!--cursor: pointer;-->
        <!--position: relative;-->
        <!--overflow: hidden;-->
    <!--}-->
    <!--.jbtn-file input[type=file] {-->
        <!--position: absolute;-->
        <!--top: 0;-->
        <!--right: 0;-->
        <!--min-width: 100%;-->
        <!--min-height: 100%;-->
        <!--text-align: right;-->
        <!--filter: alpha(opacity=0);-->
        <!--opacity: 0;-->
        <!--outline: none;-->
        <!--cursor: inherit;-->
        <!--display: block;-->
    <!--}-->
<!--</style>-->
