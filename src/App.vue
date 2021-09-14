<template>
  <div id="app">
    <Menu @changeMethod="getInfo" v-model="method" />
    <Get v-if="method === 'get'" />
    <Post v-else-if="method === 'post'" />
    <Delet v-else-if="method === 'delete'" />
    <Put v-else-if="method === 'put'" />
  </div>
</template>

<script>
import Menu from "./components/Menu.vue";
import Get from "./components/get.vue";
import Post from "./components/post.vue";
import Delet from "./components/delet.vue";
import Put from "./components/put.vue";

export default {
  name: "App",

  components: {
    Menu,
    Get,
    Post,
    Delet,
    Put,
  },
  data: function() {
    return {
      method: "get",
    };
  },

  methods: {
    getInfo: function(e) {
      this.method = e;
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
}
table,
th,
td {
  border: 1px solid black;
}
th {
  padding: 1em;
}
th {
  padding: 0 1em;
}
table {
  margin: auto;
}
.success {
  color: green;
}
a {
  margin: 1em;
  color: #42b983;
}
</style>
