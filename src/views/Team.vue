<template>
  <div class="team">
    <h1 class="subtitle-1 grey--text">Team</h1>
    <v-container class="my-5">

      <v-layout row wrap>
        <v-flex xs12 sm6 md4 lg3 v-for="(person, index) in team" :key="index">
          <v-card flat color="grey lighten-5" class="text-center ma-3">
            <v-responsive class="pt-4">
              <v-avatar size="100" color="grey lighten-2">
                <img :src="person.avatar" alt="person avatar icon">
              </v-avatar>
            </v-responsive>
            <v-card-text>
              <div class="subheading">{{ person.name }}</div>
              <div class="grey--text">{{ person.role }}</div>
            </v-card-text>
            <v-card-actions>
              <v-btn small text color="grey">
                <v-icon left small>mdi-message</v-icon>
                <span>Message</span>
              </v-btn>
            </v-card-actions>
          </v-card>
        </v-flex>
      </v-layout>

    </v-container>
  </div>
</template>

<script>
// @ is an alias to /src

export default {
  name: 'Team',
  data() {
    return {
      team: [
        { name: "Lascoyle", role: "Web Developer", avatar: require('../assets/lascoyle-avatar.jpg')},
        { name: "Marvin", role: "Social Media Maverick", avatar: require('../assets/marvin-avatar.png')},
        { name: "Jenny", role: "Graphic Designer", avatar: require('../assets/jenny-avatar.png')},
        { name: "Jane", role: "Web Developer", avatar: require('../assets/jane-avatar.png')},
        { name: "Harry", role: "Sales Guru", avatar: require('../assets/harry-avatar.png')}
      ]
    }
  }
}
</script>