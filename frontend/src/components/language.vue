<template>
    <v-form ref="form" v-model="valid" lazy-validation>

        <v-select
                v-model="first_select"
                :items="first_items"
                :rules="[v => !!v || 'Item is required']"
                label="from what language?"
                required
        ></v-select>

        <v-select
                v-model="second_select"
                :items="second_items"
                :rules="[v => !!v || 'Item is required']"
                label="to what language?"
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
                'Item 1',
                'Item 2',
                'Item 3',
                'Item 4'
            ],
            second_select: null,
            second_items: [
                'Item 1',
                'Item 2',
                'Item 3',
                'Item 4'
            ],
        }),

        methods: {
            submit () {
                if (this.$refs.form.validate()) {
                    // Native form submission is not yet supported
                    axios.post('/api/submit', {
                        from: this.first_select,
                        to: this.second_select
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
