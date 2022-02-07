<template>
  <div v-if="video">
    <iframe :src="videoURL" />
    <div class="details">
      <h4>{{ video.snippet.title }}</h4>
      <p>{{ video.snippet.description }}</p>
    </div>
  </div>
</template>

<script>
export default {
  name: "VideoDetail",
  props: ["video"],
  computed: {
    videoURL() {
      const videoId = this.video.id.videoId;
      return "https://www.youtube.com/embed/" + videoId;
    },
  },
};
</script>

<style scoped>
.details {
  margin-top: 10px;
  padding: 10px;
  border: 1px solid #ddd;
  border-radius: 4px;
}
iframe {
  width: 100%;
  height: 400px;
}
</style>
