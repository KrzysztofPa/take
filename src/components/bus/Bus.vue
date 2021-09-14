<template>
  <div id="app">
    <p>Bus</p>

    <Menu @changeMethod="getInfo" v-model="method" />
    <Get v-if="method === 'get'" />
    <Post v-else-if="method === 'post'" />
    <Delet v-else-if="method === 'delete'" />
    <Put v-else-if="method === 'put'" />
  </div>
</template>

<script>
import Menu from "./Menu.vue";
import Get from "./get.vue";
import Post from "./post.vue";
import Delet from "./delet.vue";
import Put from "./put.vue";

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

<style></style>
