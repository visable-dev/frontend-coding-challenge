<template>
  <img class="photo" :src="imgSrc" alt="Mars Rover Photos" />
</template>

<script>
export default {
  name: "Photo",
  props: {
    imgSrc: String,
  },
};
</script>

<style scoped>
  .photo {
    display: block;
    width: 22.5rem;
    margin-bottom: 5px;
  }
</style>
