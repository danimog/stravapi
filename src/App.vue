<template>
  <v-app>
    <v-app-bar
      app
      color="warning"
      light
    >
      <div class="d-flex align-center">
        <v-icon>mdi-run-fast</v-icon>
        Strava-API..
      </div>

      <v-spacer></v-spacer>

      <!-- <v-btn
        href="https://github.com/vuetifyjs/vuetify/releases/latest"
        target="_blank"
        text
      >
        <span class="mr-2">Latest Release</span>
        <v-icon>mdi-open-in-new</v-icon>
      </v-btn> -->
    </v-app-bar>

    <v-main>
      <MyHome />
    </v-main>
  </v-app>
</template>

<script>
import MyHome from './components/MyHome.vue';

export default {
  name: 'App',

  components: {
    MyHome,
  },

  data: () => ({
    //
  }),
};
</script>
