<template>
  <div>
    <input @input="onInput" />
  </div>
</template>

<script>
export default {
  name: "SearchBar",
  methods: {
    onInput: function (event) {
      this.$emit("termChange", event.target.value);
    },
  },
};
</script>

<style scoped>
input {
  width: 70%;
  height: 27px;
}

div {
  margin: 20px;
}
</style>
