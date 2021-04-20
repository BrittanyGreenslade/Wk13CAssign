<template>
  <!-- calling the function that notifies the parent element that its annoying child 
    is crying  -->
  <!-- grabs the song title and artist out of songObject prop to display on the page -->
  <!-- have to put selectedSongObject because that's the name of the prop, but still want 
    to grab just the title and artist out of that object -->
  <div id="selectionContainer">
    <h3 @click="playlistNotifyParent">{{ selectedSongObj.title }}</h3>
    <p>{{ selectedSongObj.artist }}</p>
  </div>
</template>
<script>
export default {
  name: "play-list-item",
  props: {
    selectedSongObj: Object,
  },
  //tells fn in parent what to do when an item is clicked in playlist to be removed back to song list
  methods: {
    playlistNotifyParent: function() {
      this.$emit("removeFromPlaylistClicked", this.selectedSongObj);
    },
  },
};
</script>

<style scoped></style>
