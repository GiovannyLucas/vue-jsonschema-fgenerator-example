<template>
  <v-app>
    <v-app-bar app>
      <v-toolbar-title class="headline text-uppercase">
        <span class="font-weight-light">VUE FROM GENERATOR</span>
      </v-toolbar-title>
      <v-spacer></v-spacer>
      <router-link to="/">
        <v-btn
          text
        >
          <span class="mr-2">Home</span>
        </v-btn>
      </router-link>
      <router-link to="/">
        <v-btn
          text
        >
          <span class="mr-2">Visualizar</span>
        </v-btn>
      </router-link>
    </v-app-bar>

    <v-content class="dark">
      <router-view/>
    </v-content>
  </v-app>
</template>

<script>
export default {
  components: {

  },
  data: () => ({
    //
  }),
};
</script>

<style scoped>
</style>
