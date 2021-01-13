<template>
    <v-dialog max-width="600px" v-model="dialog">
        <template v-slot:activator="{on, attrs}">
            <v-btn text class="success" v-bind="attrs" v-on="on">Add a new project</v-btn>
        </template>
        <v-card>
            <v-card-title>
                <h2>Add a new project</h2>
            </v-card-title>
            <v-card-text>
                <v-form class="px-3" ref="form">
                    <v-text-field label="Title" v-model="title" prepend-icon="mdi-folder" :rules="inputRules"></v-text-field>
                    <v-textarea label="Informations" v-model="content" prepend-icon="mdi-pencil" :rules="inputRules"></v-textarea>

                    <v-menu offset-y min-width="auto" transition="scale-transition">
                        <template v-slot:activator="{on, attrs}">
                            <v-text-field :rules="inputRules" :value="formatDate" v-bind="attrs" v-on="on" label="Due date" prepend-icon="mdi-calendar-month"></v-text-field>
                        </template>
                        <v-date-picker v-model="due">
                            <v-spacer></v-spacer>
                            <v-btn text color="primary" @click="menu = false">Cancel</v-btn>
                            <v-btn text color="primary" @click="$refs.menu.save(date)">OK</v-btn>
                        </v-date-picker>
                    </v-menu>

                    <v-btn text class="success mx-0 mt-3" @click="submit" :loading="loading">Add project</v-btn>
                </v-form>
            </v-card-text>
        </v-card>
    </v-dialog>
</template>

<script>
import format from 'date-fns/format'
import parseISO from 'date-fns/parseISO'
import db from '../firebase-conf'

export default {
    data() {
        return {
            title: '',
            content: '',
            due: null,
            inputRules: [
                value => value.length >= 3 || 'Minimum length is 3 characters'
            ],
            loading: false,
            dialog: false
        }
    },
    methods: {
        submit() {
            if(this.$refs.form.validate()) {
                const project = {
                    title: this.title,
                    content: this.content,
                    due: format(parseISO(this.due), 'eee MMM d yyyy'),
                    person: 'Lascoyle',
                    status: 'ongoing'
                };

                db.collection('projects').add(project, this.loading = true).then(() => {
                    this.loading = false;
                    this.dialog = false;
                });

            }
        }
    },
    computed: {
        formatDate() {
            return this.due ? format(parseISO(this.due), 'eee MMM d yyyy') : '';
        }
    }
}
</script>