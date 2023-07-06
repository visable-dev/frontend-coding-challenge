<template>
  <div id="app">
    <Sidebar @rover-selected="changeRover" />
    <div class="main">
      <img class="main__logo" alt="Vue logo" src="@/assets/logo.png" />
      <ListingPhotos :selected-rover="selectedRover" />
    </div>
  </div>
</template>

<script>
import ListingPhotos from "./components/ListingPhotos.vue";
import Sidebar from "./components/Sidebar.vue";

export default {
  name: "App",
  components: {
    Sidebar,
    ListingPhotos,
  },
  data: () => {
    return {
      selectedRover: "curiosity",
    };
  },
  methods: {
    changeRover(choice) {
      this.selectedRover = choice;
    },
  }
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  display: flex;
}

@media screen and (max-width: 720px) {
  #app {
    flex-flow: column;
  }
}

.main {
  flex: 0.8;
}

@media screen and (max-width: 720px) {
  .main {
    flex: 1;
  }
}

.main__logo {
  display: block;
  width: 250px;
  margin: 0 auto 40px;
}
</style>
