<template>
  <!-- id for styling -->
  <div id="sectionContainer">
    <div id="songList">
      <h1>Song List</h1>
      <div id="songContainer">
        <!-- calling function that listens for the click in the 'SongList container' -->
        <!-- loops through song songItems to grab each individual song by its id -->
        <!-- binding the attribute 'songObject' to each song so it knows which data to expect
        from its parent (comes from 'props' in 'SongList component')  -->
        <song-list
          @songAddClicked="handleSongAddClick"
          v-for="song in songItems"
          :key="song.id"
          :songObject="song"
        />
      </div>
    </div>
    <div id="playListContainer">
      <h1>Playlist</h1>
      <!-- id needed to grab element and put the item that was clicked into -->
      <play-list id="playList" :selectedSong="selectedSong" />
    </div>
  </div>
</template>

<script>
//importing the other components
import PlayList from "./PlayList.vue";
import SongList from "./SongList.vue";
//declaring components withing page-body component
export default {
  name: "page-body",
  components: {
    SongList,
    PlayList,
  },
  //store all data in the parent element
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
      selectedSong: {
        title: undefined,
        artist: undefined,
      },
    };
  },
  //function that is called when the notify parent function in 'SongList' component is called
  //and what to do here when that happens
  //it takes in the data as an argument (which is whatever is emitted on click in fn in child)
  methods: {
    removeFromSongList: function(id) {
      this.songItems.shift(id);
    },
    handleSongAddClick: function(data) {
      // console.log(data);
      this.selectedSong.title = `${data.title}`;
      this.selectedSong.artist = `${data.artist}`;
      this.removeFromSongList(data.id);
      // document.getElementById("playList").innerHTML += `<h3>${data.title}</h3>`;
      // document.getElementById("playList").innerHTML += `<p>${data.artist}</p>`;
    },
  },
};
</script>

<style scoped>
h1 {
  text-decoration: underline;
}
#playListContainer {
  border: 1px solid black;
}
#sectionContainer {
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
