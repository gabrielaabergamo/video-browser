<template>
  <ul>
    <VideoListItem
      v-for="video in myVideoList"
      v-bind:key="video.etag"
      v-bind:video="video"
      @videoSelect="onVideoSelect"
    ></VideoListItem>
  </ul>
</template>

<script>
import VideoListItem from "./VideoListItem.vue";

export default {
  name: "VideoList",
  components: {
    VideoListItem,
  },
  props: {
    myVideoList: Array,
  },
  methods: {
    onVideoSelect(video) {
      this.$emit("videoSelect", video);
    },
  },
};
</script>

<style scoped>
ul {
  list-style-type: none;
  padding: 0;
  border: 1px solid #ddd;
  margin: 0;
  width: 40%;
}
</style>
