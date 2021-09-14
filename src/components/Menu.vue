<template>
  <div class="links">
    <a href="/get">get</a>
    <a href="/post">post</a>
    <a href="/delete">delete</a>
    <a href="/put">put</a>
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
