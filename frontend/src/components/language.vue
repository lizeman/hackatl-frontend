<template>
    <v-form ref="form" v-model="valid" lazy-validation>

        <v-select
                v-model="first_select"
                :items="first_items"
                :rules="[v => !!v || 'Item is required']"
                label="translate from what language? Default: English"
                required
        ></v-select>

        <v-select
                v-model="second_select"
                :items="second_items"
                :rules="[v => !!v || 'Item is required']"
                label="translate to what language? Default: Italian"
                required
        ></v-select>

        <v-btn
                :disabled="!valid"
                @click="submit"
        >
            submit
        </v-btn>
        <v-btn @click="clear">clear</v-btn>
    </v-form>
</template>

<script>
    import axios from 'axios'

    export default {
        data: () => ({
            valid: true,
            first_select: null,
            first_items: [
                'en',
                'es',
                'it',
                'az',
                'fr',
                'de',
                'el',
                'ro',
                'lv',
                'nl'
            ],
            second_select: null,
            second_items: [
                'en',
                'es',
                'it',
                'az',
                'fr',
                'de',
                'el',
                'ro',
                'lv',
                'nl'
            ],
        }),

        methods: {
            submit () {
                if (this.$refs.form.validate()) {
                    // Native form submission is not yet supported
                    axios.get('http://128.61.45.90:8080/setFromTo', {
                        params: {
                            from: this.first_select,
                            to:  this.second_select
                        }
                    })
                }
            },
            clear () {
                this.$refs.form.reset()
            }
        }
    }
</script>

<style scoped>

</style>
