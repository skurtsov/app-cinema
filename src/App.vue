<template>
  <div
    class="screen"
    :style="{ 'background-image': 'url(' + current_BG + ')' }"
  >
    <div class="overlay-bg"></div>
    <div class="name-film">
      <h1>{{ current_Title }}</h1>
    </div>

    <div class="cards">
      <div
        class="card"
        v-for="(idx, key) in films"
        :key="key"
        :style="{ backgroundImage: 'url(' + f_data[key] + ')' }"
        v-on:click="changeFilm(key)"
      >
        <div class="age"></div>
        <div class="trid"></div>
      </div>
    </div>

    <ModalWindow :UrlTitle="current_Trailer" />
  </div>
</template>

<script>
import data from "../data.json";
//import image from "./assets/thumbs/0.jpg";
import ModalWindow from "./components/ModalWindow.vue";

export default {
  name: "App",
  components: {
    ModalWindow,
  },
  created() {
    this.current_BG = this.all_background[0];
    this.j_films.push(data);
    for (let i = 0; i < this.f_data.length; i++) {
      this.j_titles.push(this.j_films[0].films[i].title);
      this.j_trailers.push(this.j_films[0].films[i].trailer);
    }
    this.current_Title = this.j_titles[0];
  },
  data() {
    return {
      isModal: false,
      films: [1, 2, 3, 4, 5],
      current_BG: "",
      current_Trailer: "https://www.youtube.com/embed/s7EdQ4FqbhY",
      current_Title: "",
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
      j_titles: [],
      j_films: [],
      j_trailers: [],
    };
  },
  methods: {
    changeFilm(index) {
      this.current_BG = this.all_background[index];
      this.current_Title = this.j_titles[index];
      this.current_Trailer = this.j_trailers[index];
    },
  },
};
</script>
