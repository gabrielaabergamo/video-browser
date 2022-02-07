<template>
  <div class="container">
    <SearchBar @termChange="onTermChange"></SearchBar>
    <div class="row">
      <VideoDetail v-bind:video="selectedVideo" />
      <VideoList
        @videoSelect="onVideoSelect"
        v-bind:myVideoList="videos"
      ></VideoList>
    </div>
  </div>
</template>

<script>
import axios from "axios";
import SearchBar from "./components/SearchBar.vue";
import VideoList from "./components/VideoList.vue";
import VideoDetail from "./components/VideoDetail.vue";

const apiKey = process.env.VUE_APP_API_KEY;

export default {
  name: "App",
  components: {
    SearchBar,
    VideoList,
    VideoDetail,
  },
  data: function () {
    return {
      videos: [],
      selectedVideo: null,
    };
  },
  methods: {
    onVideoSelect(video) {
      this.selectedVideo = video;
    },
    onTermChange: function (searchTerm) {
      axios
        .get("https://www.googleapis.com/youtube/v3/search", {
          params: {
            key: apiKey,
            type: "video",
            part: "snippet",
            q: searchTerm,
          },
        })
        .then((response) => (this.videos = response.data.items));
    },
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

.container {
  box-sizing: border-box;
  width: 1000px;
  max-width: 100%;
  margin: 0 auto;
  align-items: center;
}

.row {
  display: flex;
  gap: 20px;
}
</style>
