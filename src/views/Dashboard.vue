<template>
  <div class="dashboard">
    <h1 class="subtitle-1  grey--text">Dashboard</h1>

    <v-container class="my-5">
      <v-card flat color="grey lighten-5" class="pa-3" v-for="(project, index) in projects" :key="index">
        <v-layout row wrap :class="`pa-3 project ${project.status}`">
          <v-flex xs12 md6>
            <v-card-title class="caption grey--text">{{ project.title }}</v-card-title>
            <v-card-text>Create a new website</v-card-text>
          </v-flex>
          <v-flex xs6 sm4 md2>
            <v-card-title class="caption grey--text">{{ project.person }}</v-card-title>
            <v-card-text>Lascoyle</v-card-text>
          </v-flex>
          <v-flex xs6 sm4 md2>
            <v-card-title class="caption grey--text">{{ project.due }}</v-card-title>
            <v-card-text>15 Jan 2021</v-card-text>
          </v-flex>
          <v-flex xs6 sm4 md2>
            <v-card-title class="caption grey--text">{{ project.status }}</v-card-title>
            <v-card-text>Ongoing</v-card-text>
          </v-flex>
        </v-layout>
        <v-divider class="mt-3"></v-divider>
      </v-card>
    </v-container>

  </div>
</template>

<script>
export default {
  name: 'Dashboard',
  data() {
    return {
      projects: [
        { title: "Design a website", person: "Lascoyle", due: "15th Jan 2021", status: "ongoing" },
        { title: "Code up homepage", person: "Jane", due: "25th Dec 2020", status: "complete" },
        { title: "Design video thumbnails", person: "John", due: "31st Dec 2020", status: "complete" },
        { title: "Create a community forum", person: "Marvin", due: "15th Nov 2020", status: "overdue" },
      ]
    }
  }
}
</script>

<style>
.project.complete {
  border-left: 4px solid #3cd1c2;
}

.project.ongoing {
  border-left: 4px solid orange;
}

.project.overdue {
  border-left: 4px solid tomato;
}
</style>
