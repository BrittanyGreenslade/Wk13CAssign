<template>
  <div id="selectionContainer">
    <h3>{{ selectedSong.title }}</h3>
    <p>{{ selectedSong.artist }}</p>
  </div>
</template>
<script>
export default {
  name: "play-list",
  props: {
    selectedSong: Object,
  },
};
</script>

<style scoped>
div {
  height: 100vh;
  width: 100%;
}
</style>
