<template>
  <div id="selectionContainer">
    <h3>{{ selectedSongObj.title }}</h3>
    <p>{{ selectedSongObj.artist }}</p>
  </div>
</template>
<script>
export default {
  name: "play-list",
  props: {
    selectedSongObj: Object,
  },
};
</script>

<style scoped>
div {
  height: 10vh;
  width: 100%;
}
</style>
