<template>
    <v-dialog max-width="600px">
        <template v-slot:activator="{on, attrs}">
            <v-btn flat text class="success" v-bind="attrs" v-on="on">Add a new project</v-btn>
        </template>
        <v-card>
            <v-card-title>
                <h2>Add a new project</h2>
            </v-card-title>
        </v-card>
    </v-dialog>
</template>

<script>
export default {
    
}
</script>