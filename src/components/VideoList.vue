<template>
  <ul>
    oi
    <VideoListItem
      v-for="video in myVideoList"
      v-bind:key="video.etag"
      v-bind:video="video"
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
};
</script>

<style></style>
