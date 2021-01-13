<template>
    <nav>

        <v-snackbar v-model="snackbar" :timeout="4000" top color="success">
            <v-layout align-center>
                <span>Awesome! You've just added a new project!</span>
                <template>
                    <v-btn text color="white" @click="snackbar = false">Close</v-btn>
                </template>
            </v-layout>
        </v-snackbar>

        <v-app-bar text app color="grey lighten-4" class="px-2">
            <v-app-bar-nav-icon class="grey--text" @click="drawer = !drawer"></v-app-bar-nav-icon>
            <v-toolbar-title class="text-uppercase grey--text">
                <span class="font-weight-light">ToDo</span>
                <span>/Vuetify</span>
            </v-toolbar-title>
            <v-spacer></v-spacer>

            <!-- Dropdown Menu -->
            <v-menu offset-y>
                <template v-slot:activator="{ on, attrs}">
                    <v-btn text color="grey" v-bind="attrs" v-on="on">
                        <v-icon left>mdi-chevron-down</v-icon>
                        <span>Menu</span>
                    </v-btn>
                </template>
                <v-list>
                    <v-list-item v-for="(link, index) in links" :key="index" router v-bind:to="link.route">
                        <v-list-item-title class="grey--text">{{ link.text }}</v-list-item-title>
                    </v-list-item>
                </v-list>
            </v-menu>

            <v-btn text color="grey">
                <span>Sign Out</span>
                <v-icon right>mdi-exit-to-app</v-icon>
            </v-btn>
        </v-app-bar>

        <v-navigation-drawer app v-model="drawer" class="primary">
            <v-layout column align-center>
                <v-flex class="my-5">
                    <v-avatar size="128" class="mt-5">
                        <img src="../assets/lascoyle-avatar.jpg" alt="person avatar">
                    </v-avatar>
                    <p class="white--text subheading mt-3 text-center">Lascoyle</p>
                </v-flex>
                <v-flex class="mt-4 mb-4">
                    <popup @projectAdded="snackbar = true"></popup>
                </v-flex>
            </v-layout>
            <v-list>
                <v-list-item v-for="(link, index) in links" v-bind:key="index" router v-bind:to="link.route">
                    <v-list-item-action>
                        <v-icon class="white--text">{{ link.icon }}</v-icon>
                    </v-list-item-action>
                    <v-list-item-content>
                        <v-list-item-title class="white--text">{{ link.text }}</v-list-item-title>
                    </v-list-item-content>
                </v-list-item>
            </v-list>
        </v-navigation-drawer>
    </nav>
</template>

<script>
import Popup from './Popup.vue'

export default {
    components: {
        'popup': Popup
    },
    data() {
        return {
            drawer : false,
            links: [
                { icon: 'mdi-view-dashboard', text: 'Dashboard', route: '/'},
                { icon: 'mdi-folder', text: 'My Projects', route: '/projects'},
                { icon: 'mdi-account', text: 'Team', route: '/team'}
            ],
            snackbar: false
        }
    }
}
</script>