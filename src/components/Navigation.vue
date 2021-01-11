<template>
    <nav>
        <v-app-bar flat app color="grey lighten-4" class="px-2">
            <v-app-bar-nav-icon class="grey--text" @click="drawer = !drawer"></v-app-bar-nav-icon>
            <v-toolbar-title class="text-uppercase grey--text">
                <span class="font-weight-light">ToDo</span>
                <span>/Vuetify</span>
            </v-toolbar-title>
            <v-spacer></v-spacer>
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
export default {
    data() {
        return {
            drawer : false,
            links: [
                { icon: 'mdi-view-dashboard', text: 'Dashboard', route: '/'},
                { icon: 'mdi-folder', text: 'My Projects', route: '/projects'},
                { icon: 'mdi-account', text: 'Team', route: '/team'}
                ]
        }
    }
}
</script>