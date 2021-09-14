<template>
  <div class="links">
    <button @click="$emit('changeApp', 'bus')">Bus</button>
    <button @click="$emit('changeApp', 'carriage')">carriage</button>
    <button @click="$emit('changeApp', 'client')">client</button>
    <button @click="$emit('changeApp', 'route')">route</button>
  </div>
</template>

<script>
export default {
  name: "MainMenu",
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
