<template>
  <div>
    <!-- calling the function that notifies the parent element that its annoying child 
    is crying  -->
    <!-- have to put songObject now because that's the name of the prop, but still want to grab -->
    <!-- just the title and artist out of that object -->
    <div @click="notifyParent">
      <h3>{{ songObject.title }}</h3>
      <p>{{ songObject.artist }}</p>
    </div>
  </div>
</template>

<script>
export default {
  name: "song-list",
  props: {
    songObject: Object,
    // title: String,
    // artist: String,
  },
  methods: {
    // function to notify the method songAddClicked in the parent element of what data
    //to grab on click
    notifyParent: function() {
      this.$emit("songAddClicked", this.songObject);
    },
  },
};
</script>

<style scoped></style>
