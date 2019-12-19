
<template>
  <v-app>
    <v-app-bar
      app
      color="green"
      dark
    >
      <div class="d-flex align-center">
        <v-img
          alt="Vuetify Logo"
          class="shrink mr-2"
          contain
          src="/tura_logo.png"
          transition="scale-transition"
          width="50"
        />

        <h1> Fotobox </h1>
      </div>

      <v-spacer></v-spacer>

      
    </v-app-bar>

    <v-content>
      <HelloWorld/>
    </v-content>
  </v-app>
</template>

<script>
import HelloWorld from './components/HelloWorld';

export default {
  name: 'App',

  components: {
    HelloWorld,
  },

  data: () => ({
    //
  }),
};
</script>

<style scoped>
@import url('https://fonts.googleapis.com/css?family=Anton&display=swap');

h1 {
font-family: 'Anton', sans-serif;
}
</style>
