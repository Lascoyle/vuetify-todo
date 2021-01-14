<template>
  <div class="dashboard px-2">
    <h1 class="subtitle-1  grey--text">Dashboard</h1>

    <v-container class="my-5">

      <v-layout row class="mb-3">
        <v-tooltip top>
          <template v-slot:activator="{ on, attrs }">
            <v-btn small text color="grey" @click="sortByTitle()" v-on="on" v-bind="attrs">
              <v-icon left small>mdi-folder</v-icon>
              <span class="caption text-lowercase">by project name</span>
            </v-btn>
          </template>
          <span>Sort projects by project name</span>
        </v-tooltip>

        <v-tooltip top>
          <template v-slot:activator="{ on, attrs }">
            <v-btn small text color="grey" @click="sortByPerson()" v-on="on" v-bind="attrs">
              <v-icon left small>mdi-account</v-icon>
              <span class="caption text-lowercase">by person</span>
            </v-btn>
          </template>
          <span>Sort projects by person</span>
        </v-tooltip>

        <v-tooltip top>
          <template v-slot:activator="{ on, attrs }">
            <v-btn small text color="grey" @click="sortByDate()" v-on="on" v-bind="attrs">
              <v-icon left small>mdi-account</v-icon>
              <span class="caption text-lowercase">by date due</span>
            </v-btn>
          </template>
          <span>Sort projects by date due</span>
        </v-tooltip>
      </v-layout>

      <v-card text color="grey lighten-5" class="pa-3" v-for="(project, index) in projects" :key="index">
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
            <v-card-title class="caption grey--text">Due by</v-card-title>
            <v-card-text>{{ project.due }}</v-card-text>
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
import db from '../firebase-conf'

export default {
  name: 'Dashboard',
  data() {
    return {
      projects: []
    }
  },
  methods: {
    sortByTitle() {
      this.projects.sort((a,b) => a.title < b.title ? -1 : 1);
    },

    sortByPerson() {
      this.projects.sort((a,b) => a.person < b.person ? -1 : 1);
    },

    sortByDate() {
      this.projects.sort((a,b) => Date(a.due) < Date(b.due) ? -1 : 1);
    }
  },
  created() {
    db.collection('projects').onSnapshot(res => {
      const changes = res.docChanges();

      changes.forEach(change => {
        if (change.type === 'added') {
          this.projects.push({
            ...change.doc.data(),
            id: change.doc.id
          });
        }
      })
    })
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
