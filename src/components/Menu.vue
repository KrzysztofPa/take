<template>
  <div class="links">
    <button @click="$emit('changeMethod', 'get')">get</button>
    <button @click="$emit('changeMethod', 'post')">post</button>
    <button @click="$emit('changeMethod', 'delete')">delete</button>
    <button @click="$emit('changeMethod', 'put')">put</button>
  </div>
</template>

<script>
export default {
  name: "Menu",
};
</script>

<style scoped>
.links {
  display: flex;
  justify-content: center;
}
a {
  margin: 1em;
  color: #42b983;
}
</style>
