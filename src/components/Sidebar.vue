<template>
  <aside class="sidebar">
    <p class="sidebar__label" for="rover-select">Choose a Rover:</p>
    <select
      id="rover-select"
      class="sidebar__select"
      v-model="selectedRover"
      @change="changeRover"
    >
      <option value="curiosity">Curiosity</option>
      <option value="opportunity">Opportunity</option>
      <option value="spirit">Spirit</option>
    </select>
  </aside>
</template>

<script>
export default {
  name: "Sidebar",
  data: () => {
    return {
      selectedRover: "curiosity",
    };
  },
  methods: {
    changeRover() {
      this.$emit("rover-selected", this.selectedRover);
    },
  }
};
</script>

<style scoped>
.sidebar {
  background: #e3e3e3;
  flex: 0.2;
}

@media screen and (max-width: 720px) {
  .sidebar {
    flex: 1;
  }
}

.sidebar__select {
  width: 70%;
  padding: 8px 3px;
}
</style>
