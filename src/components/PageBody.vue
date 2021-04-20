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
        <song-item
          @songAddClicked="handleSongAddClick"
          v-for="song in songItems"
          :key="song.id"
          :songObject="song"
        />
      </div>
    </div>
    <div id="playList">
      <h1>Playlist</h1>
      <!-- loops through "selected songs" and gives a key to them (which is their id), 
      //then adds the attribute selectedSongObj to them -->
      <div id="playListContainer">
        <play-list-item
          v-for="selectedSong in selectedSongs"
          :key="selectedSong.id"
          :selectedSongObj="selectedSong"
        />
      </div>
    </div>
  </div>
</template>

<script>
//importing the other components
import PlayListItem from "./PlayListItem.vue";
import SongItem from "./SongItem.vue";
//declaring components withing page-body component
export default {
  name: "page-body",
  components: {
    SongItem,
    PlayListItem,
  },
  //store all data in the parent element
  data() {
    return {
      // stores the songlist song objects in an array
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
      //stores the playlist song objects in an array
      selectedSongs: [
        //   {
        //   title: undefined,
        //   artist: undefined,
        // }
      ],
    };
  },

  methods: {
    //function to remove the song that was clicked from the playlist
    //filters out the songs whose ids don't match the id of the song object that was clicked
    //if the ids match, return false; if not, return true. store all of that in a variable
    //called notRemovedSongs and udpates the 'songItems' list to the filtered out songs
    //aka all songs not cliceked
    removeFromSongList: function(id) {
      let notRemovedSongs = this.songItems.filter(function(song) {
        if (song.id === id) {
          return false;
        } else if (song.id !== id) {
          return true;
        }
      });
      this.songItems = notRemovedSongs;
    },
    //function that is called when the notifyParent fn in 'SongList' component is called,
    //and what to do in this component when that happens. it takes in the data as an
    //argument (which is whatever is emitted on click in fn in child - the object)
    handleSongAddClick: function(data) {
      this.selectedSongs.push(data);
      this.removeFromSongList(data.id);
    },
    //working on a remove from playlist fn but not done yet
    // handleRemoveFromPlaylist: function(data1) {
    //   console.log(data1);
    // },
    //@removeFromPlaylistClicked="handleRemoveFromPlaylist"
  },
};
</script>

<style scoped>
h1 {
  text-decoration: underline;
}

#sectionContainer {
  display: grid;
  grid-template-columns: 1fr 1fr;
  width: 90vw;
  height: 80vh;
}

#songContainer,
#playListContainer {
  display: grid;
}
#songList,
#playList {
  border: 1px solid black;
}
</style>
