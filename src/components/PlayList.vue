<template>
  <div>
    <h3>{{ title }}</h3>
    <p>{{ artist }}</p>
  </div>
</template>

<script>
export default {
  name: "play-list",
  props: {
    title: String,
    artist: String,
  },
};
</script>

<style scoped>
h1 {
  text-decoration: underline;
}
div {
  height: 100vh;
  width: 100%;
}
</style>
