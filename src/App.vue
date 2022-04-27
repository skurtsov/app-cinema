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
        :style="{ 'background-image': 'url(' + image + ')' }"
      >
        {{ films[key] }}
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "App",
  data() {
    return {
      films: [1, 2, 3, 4, 5],
      current_BG: require("@/assets/0.jpg"),
    };
  },
};
</script>
