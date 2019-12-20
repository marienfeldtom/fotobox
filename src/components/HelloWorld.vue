<template>
<div>
  <loading :active.sync="isLoading" 
        :can-cancel="true" 
        :on-cancel="onCancel"
        :is-full-page="fullPage"></loading>
  <v-container>
    <v-layout text-center wrap>
      <ImageAnzeige />

      <v-flex xs12 mb-5>
        <h1 class="display-2 font-weight-bold mt-12">Neues Foto</h1>

        <v-layout justify-center>
          <v-btn @click="startTimer()" class="mx-2 mt-12" fab dark x-large color="green">
            <v-icon dark>mdi-plus</v-icon>
          </v-btn>
        </v-layout>
      </v-flex>
    </v-layout>
    <v-overlay :value="overlay">
      <div id="time">{{time}}</div>
    </v-overlay>
  </v-container>
  </div>
</template>

<script>
import ImageAnzeige from "./Image";
import Loading from 'vue-loading-overlay';
import 'vue-loading-overlay/dist/vue-loading.css';
const axios = require("axios");

export default {
  components: {
    ImageAnzeige, Loading
  },

  name: "HelloWorld",
  data() {
    return {
      overlay: false,
      time: 5,
       isLoading: false,
       fullPage: true
    };
  },
  methods: {
    startTimer: function() {
      this.overlay = true;
      if (this.time == 1) {
        // Make a request for a user with a given ID
        this.isLoading = true;
        axios.get("http://192.168.178.44:3000/").finally(function() {
          this.isLoading = false;
        });
      }
      if (this.time > 0) {
        setTimeout(() => {
          this.time -= 1;
          this.startTimer();
        }, 1000);
      } else {
        this.overlay = false;
        this.time = 5;
      }
    }
  }
};
</script>

<style scoped>
#time {
  font-size: 200px;
}
.v-btn {
  height: 150px !important;
  width: 150px !important;
}
</style>