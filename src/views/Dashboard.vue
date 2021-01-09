<template>
  <div class="dashboard">
    <h1 class="subtitle-1  grey--text">Dashboard</h1>

    <v-container class="my-5">

      <v-layout row class="mb-3">
        <v-btn small text color="grey" @click="sortBy('title')">
          <v-icon left small>mdi-folder</v-icon>
          <span class="caption text-lowercase">by project name</span>
        </v-btn>
        <v-btn small text color="grey" @click="sortBy('person')">
          <v-icon left small>mdi-account</v-icon>
          <span class="caption text-lowercase">by person</span>
        </v-btn>
      </v-layout>

      <v-card flat color="grey lighten-5" class="pa-3" v-for="(project, index) in projects" :key="index">
        <v-layout row wrap :class="`pa-3 project ${project.status}`">
          <v-flex xs12 md6>
            <v-card-title class="caption grey--text">Project</v-card-title>
            <v-card-text>{{ project.title }}</v-card-text>
          </v-flex>
          <v-flex xs6 sm4 md2>
            <v-card-title class="caption grey--text">Person</v-card-title>
            <v-card-text>{{ project.person }}</v-card-text>
          </v-flex>
          <v-flex xs6 sm4 md2>
            <v-card-title class="caption grey--text">{{ project.due }}</v-card-title>
            <v-card-text>15 Jan 2021</v-card-text>
          </v-flex>
          <v-flex xs6 sm4 md2>
            <div class="float-right mr-5">
              <v-card-title class="caption grey--text pb-2">Status</v-card-title>
              <v-chip :class="`${project.status} white--text caption`">{{ project.status }}</v-chip>
            </div>
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
  },
  methods: {
    sortBy(prop) {
      this.projects.sort((a,b) => a[prop] < b[prop] ? -1 : 1)
    }
  }
}
</script>

<style>
.project.complete {
  border-left: 7px solid #3cd1c2;
}

.project.ongoing {
  border-left: 7px solid orange;
}

.project.overdue {
  border-left: 7px solid tomato;
}

.v-chip--no-color.complete {
  background-color: #3cd1c2!important;
}

.v-chip--no-color.ongoing {
  background-color: orange!important;
}

.v-chip--no-color.overdue {
  background-color: tomato!important;
}
</style>
