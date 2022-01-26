<template>
    <div>
        <v-app-bar
        dense
        flat
        outlined
        shrink-on-scroll
        color="blue lighten-1"
        >
        <template #extension>
            <v-tabs optional>
            <v-tab to="/users/sign-up" class="white--text ">Sigun Up</v-tab>
            <v-tab to="/users/sign-in" class="white--text ">Sign In</v-tab>
            </v-tabs>
        </template>
        </v-app-bar>
    </div>
</template>

<script>
    export default {
        name: 'Header'
    }
</script>