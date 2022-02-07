<template>
  <li @click="onVideoSelect">
    <img :src="thumbnailUrl" />
    {{ video.snippet.title }}
  </li>
</template>

<script>
export default {
  name: "VideoListItem",
  props: ["video"],
  computed: {
    thumbnailUrl() {
      return this.video.snippet.thumbnails.default.url;
    },
  },
  methods: {
    onVideoSelect() {
      this.$emit("videoSelect", this.video);
    },
  },
};
</script>

<style scoped>
li {
  padding: 8px 16px;
  border-bottom: 1px solid #ddd;
  display: flex;
  gap: 7px;
  cursor: pointer;
}
li:last-child {
  border-bottom: none;
}
li:hover {
  background-color: #eee;
}
</style>
