<template>
  <div>
    <SearchBar @termChange="onTermChange"></SearchBar>
    <VideoList v-bind:myVideoList="videos"></VideoList>
  </div>
</template>

<script>
import axios from "axios";
import SearchBar from "./components/SearchBar.vue";
import VideoList from "./components/VideoList.vue";

const apiKey = process.env.VUE_APP_API_KEY;

export default {
  name: "App",
  components: {
    SearchBar,
    VideoList,
  },
  data: function () {
    return {
      videos: [],
    };
  },
  methods: {
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
</style>
