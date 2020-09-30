<template>
  <v-app>
    <v-content>
      <v-toolbar class="indigo accent-3">
        <v-toolbar-title class="ml-8">
          <span class="grey--text text--lighten-1"> Bhavuk</span>
          <span class="grey--text text--lighten-2">Garg</span>
        </v-toolbar-title>
      </v-toolbar>
      <v-main>
        <calculator />
      </v-main>
    </v-content>
  </v-app>
</template>

<script>
import Calculator from "./components/Calculator";

export default {
  name: "App",

  components: {
    Calculator,
  },

  data: () => ({
    //
  }),
};
</script>
