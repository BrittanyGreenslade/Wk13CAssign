<template>
  <div>
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
    notifyParent: function() {
      this.$emit("songAddClicked", this.title);
      this.$emit("songAddClicked", this.artist);
    },
  },
};
</script>

<style scoped></style>
