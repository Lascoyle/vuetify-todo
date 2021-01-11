<template>
  <div class="projects">
    <h1 class="subtitle-1  grey--text">Projects</h1>

    <v-container class="my-5">

      <v-expansion-panels>
        <v-expansion-panel v-for="(project, index) in myProjects" :key="index">
          <v-expansion-panel-header>
            {{ project.title }}
          </v-expansion-panel-header>
          <v-expansion-panel-content class="px-4 grey--text">
            <div class="font-weight-bold">due by {{ project.due }}</div>
            <div>{{ project.content }}</div>
          </v-expansion-panel-content>
        </v-expansion-panel>
      </v-expansion-panels>

    </v-container>
  </div>
</template>

<script>
// @ is an alias to /src

export default {
  name: 'Projects',
  data() {
    return {
      projects: [
        { title: "Design a website", person: "Lascoyle", due: new Date(2021, 0, 15).toDateString(), status: "ongoing", content: "Lorem, ipsum dolor sit amet consectetur adipisicing elit. Dolorem odit sed ullam velit recusandae harum praesentium alias dolores eveniet. Facere illum quas blanditiis ipsa, laborum recusandae alias quidem placeat assumenda?" },
        { title: "Code up homepage", person: "Jane", due: new Date(2020, 11, 25).toDateString(), status: "complete", content: "Lorem, ipsum dolor sit amet consectetur adipisicing elit. Dolorem odit sed ullam velit recusandae harum praesentium alias dolores eveniet. Facere illum quas blanditiis ipsa, laborum recusandae alias quidem placeat assumenda?" },
        { title: "Design video thumbnails", person: "Jenny", due: new Date(2020, 11, 31).toDateString(), status: "complete", content: "Lorem, ipsum dolor sit amet consectetur adipisicing elit. Dolorem odit sed ullam velit recusandae harum praesentium alias dolores eveniet. Facere illum quas blanditiis ipsa, laborum recusandae alias quidem placeat assumenda?" },
        { title: "Create a community forum", person: "Marvin", due: new Date(2020, 10, 13).toDateString(), status: "overdue", content: "Lorem, ipsum dolor sit amet consectetur adipisicing elit. Dolorem odit sed ullam velit recusandae harum praesentium alias dolores eveniet. Facere illum quas blanditiis ipsa, laborum recusandae alias quidem placeat assumenda?" },
        { title: "Design a new Vue.js application", person: "Lascoyle", due: new Date(2021, 2, 2).toDateString(), status: "ongoing", content: "Lorem, ipsum dolor sit amet consectetur adipisicing elit. Dolorem odit sed ullam velit recusandae harum praesentium alias dolores eveniet. Facere illum quas blanditiis ipsa, laborum recusandae alias quidem placeat assumenda?" },
      ]
    }
  },
  computed: {
    myProjects() {
      return this.projects.filter(project => {
        return project.person === 'Lascoyle'
      })
    }
  }
}
</script>
