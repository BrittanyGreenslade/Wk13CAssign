<template>
  <div>
    <!-- calling the function that notifies the parent element that its annoying child 
    is crying  -->
    <!-- grabs the song title and artist out of songObject prop to display on the page -->
    <!-- have to put songObject because that's the name of the prop, but still want to grab -->
    <!-- just the title and artist out of that object -->
    <div @click="notifyParent">
      <h3>{{ songObject.title }}</h3>
      <p>{{ songObject.artist }}</p>
    </div>
  </div>
</template>

<script>
export default {
  name: "song-item",
  props: {
    songObject: Object,
  },
  methods: {
    // function to notify the method 'songAddClicked' (in the parent element) of what data
    //to grab on click - data being the songObject that is clicked
    notifyParent: function() {
      this.$emit("songAddClicked", this.songObject);
    },
  },
};
</script>

<style scoped></style>
