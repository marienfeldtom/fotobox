<template>
  <v-container>
    <v-layout text-center wrap>
      <v-flex xs12>
        <v-img src="https://via.placeholder.com/1600x900" class="my-3" contain height="400"></v-img>
      </v-flex>

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
</template>

<script>
export default {
  name: "HelloWorld",
  data() {
    return {
      overlay: false,
      time: 5
    };
  },
  methods: {
    startTimer: function() {
      this.overlay= true;
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