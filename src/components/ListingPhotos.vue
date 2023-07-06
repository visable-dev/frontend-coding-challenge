<template>
  <div class="listingPhotos">
    <div class="listingPhotos__grid">
      <Photo v-for="(photo, index) in photos" :key="index" :imgSrc="photo.img_src" />
    </div>
    <button
      class="listingPhotos__btn"
      v-if="photos.length > 0"
      @click="morePhotos"
    >
      More Photos
    </button>
  </div>
</template>

<script>
import Photo from "./Photo.vue";
import axios from "axios";
const API_KEY = "JT8B7UcIq8yWg8hLiwCLrha7euHmXzM0md8YjzIv";

export default {
  components: {
    Photo,
  },
  props: {
    selectedRover: String,
  },
  data() {
    return {
      photos: [],
      page: 1,
    };
  },
  mounted() {
    this.getPhotos
  },
  watch: {
    selectedRover() {
      console.log(this.selectedRover)
      this.getPhotos();
    },
  },
  methods: {
    getPhotos() {
      this.photos = [];
      axios
        .get(`https://api.nasa.gov/mars-photos/api/v1/rovers/${this.selectedRover}/photos?sol=1000&page=${this.page}&api_key=${API_KEY}`)
        .then((response) => {
          console.log(response.data.photos.length)
          console.log('next', response)
          this.photos = this.photos.concat(response.data.photos);
        });

    },
    morePhotos() {
      this.page++;
      this.getPhotos();
    },
  },
};
</script>

<style scoped>
.listingPhotos {
  max-width: 90%;
  margin: 0 auto;
}
.listingPhotos__grid {
  margin-bottom: 30px;
  display: grid;
  grid-template-columns: repeat(auto-fill, 33%);
  grid-gap: 5px;
}

@media screen and (max-width: 720px) {
  .listingPhotos__grid {
    grid-template-columns: repeat(auto-fill, 99%);
  }
}
.listingPhotos__btn {
  border: 1px solid #000;
  width: 180px;
  padding: 10px 0;
  text-transform: uppercase;
  font-weight: bold;
  background-color: #fff;
  cursor: pointer;
}
</style>
