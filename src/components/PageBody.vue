<template>
  <div id="sectionContainer">
    <div id="songList">
      <h1>Song List</h1>
      <div id="songContainer">
        <song-list
          @songAddClicked="handleSongAddClick"
          v-for="song in songItems"
          :key="song.id"
          :title="song.title"
          :artist="song.artist"
        />
      </div>
    </div>
    <div>
      <h1>Playlist</h1>
      <play-list id="playList" />
    </div>
    <!-- <div id="songListSection" v-for="song in songItems" :key="song.id">
      <h2>{{ song.title }}</h2>
      <h3>{{ song.artist }}</h3>
    </div> -->
  </div>
</template>

<script>
import PlayList from "./PlayList.vue";
import SongList from "./SongList.vue";
export default {
  name: "page-body",
  components: {
    SongList,
    PlayList,
  },
  methods: {
    handleSongAddClick: function(data) {
      console.log(data);
      document.getElementById("playList").innerHTML += `<h3>${data}</h3>`;
    },
  },
  data() {
    return {
      songItems: [
        {
          title: `The Neon Skyline`,
          artist: `Andy Schauf`,
          id: 1,
        },
        {
          title: `Old News`,
          artist: `BROCKHAMPTON`,
          id: 2,
        },
        {
          title: `Edmonton`,
          artist: `The Rural Alberta Advantage`,
          id: 3,
        },
        {
          title: `Slow Craft`,
          artist: `Pigeon Hole`,
          id: 4,
        },
        {
          title: `Dearly Departed`,
          artist: `Shakey Graves`,
          id: 5,
        },
        {
          title: `Old Friends`,
          artist: `Pinegrove`,
          id: 6,
        },
        {
          title: `Empty`,
          artist: `Kevin Abstract`,
          id: 7,
        },
        {
          title: `Tactile`,
          artist: `Ftmlss`,
          id: 8,
        },
        {
          title: `I Look Like a Nightmare`,
          artist: `BLU KOBINA`,
          id: 9,
        },
        {
          title: `Stargazer`,
          artist: `Tommy Newport, EARTHGANG`,
          id: 10,
        },
      ],
    };
  },
};
</script>

<style scoped>
h1 {
  text-decoration: underline;
}
#sectionContainer {
  border: 1px solid black;
  display: grid;
  grid-template-columns: 1fr 1fr;
  width: 90vw;
}
#songContainer {
  display: grid;
}
#songList {
  border: 1px solid black;
}
</style>
