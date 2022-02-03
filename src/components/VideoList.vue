<template>
  <ul>
    oi
    <VideoListItem />
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
