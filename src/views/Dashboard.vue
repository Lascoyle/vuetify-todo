<template>
  <div class="dashboard">
    <h1 class="subtitle-1  grey--text">Dashboard</h1>

    <v-container class="my-5">
     <v-card flat color="grey lighten-5" class="pa-3">
       <v-layout row wrap>
         <v-flex xs12 md6>
           <v-card-title class="caption grey--text">Project Title</v-card-title>
           <v-card-text>Create a new website</v-card-text>
         </v-flex>
         <v-flex xs6 sm4 md2>
            <v-card-title class="caption grey--text">Person</v-card-title>
            <v-card-text>Lascoyle</v-card-text>
         </v-flex>
         <v-flex xs6 sm4 md2>
            <v-card-title class="caption grey--text">Due by</v-card-title>
            <v-card-text>15 Jan 2021</v-card-text>
         </v-flex>
         <v-flex xs6 sm4 md2>
            <v-card-title class="caption grey--text">Status</v-card-title>
            <v-card-text>Ongoing</v-card-text>
         </v-flex>
       </v-layout>
     </v-card>
    </v-container>

  </div>
</template>

<script>
// @ is an alias to /src

export default {
  name: 'Dashboard',
  components: {
    //
}
}
</script>
