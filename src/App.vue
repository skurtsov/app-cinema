<template>
  <div
    class="screen"
    :style="{ 'background-image': 'url(' + current_BG + ')' }"
  >
    <div class="name-film">
      <h1>Film</h1>
    </div>
    <div class="cards">
      <div
        class="card"
        v-for="(idx, key) in films"
        :key="key"
        :style="{ backgroundImage: 'url(' + f_data[key] + ')' }"
        v-on:click="changeFilm(key)"
      ></div>
    </div>
  </div>
</template>

<script>
//import data from "../data.json";
//import image from "./assets/thumbs/0.jpg";

export default {
  name: "App",
  created() {
    this.current_BG = this.all_background[0];
  },
  data() {
    return {
      films: [1, 2, 3, 4, 5],
      current_BG: "",
      all_background: [
        require("./assets/0.jpg"),
        require("./assets/1.jpg"),
        require("./assets/2.jpg"),
        require("./assets/3.jpg"),
        require("./assets/4.jpg"),
      ],
      f_data: [
        require("./assets/thumbs/0.jpg"),
        require("./assets/thumbs/1.jpg"),
        require("./assets/thumbs/2.jpg"),
        require("./assets/thumbs/3.jpg"),
        require("./assets/thumbs/4.jpg"),
      ],
    };
  },
  methods: {
    changeFilm(index) {
      this.current_BG = this.all_background[index];
    },
  },
};
</script>
