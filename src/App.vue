<template>
  <div id="app">
    <MainMenu @changeApp="getInfo" v-model="currentApp" />
    <Bus v-if="currentApp === 'bus'" />
    <Carriage v-else-if="currentApp === 'carriage'" />
    <Client v-else-if="currentApp === 'client'" />
    <Route v-else-if="currentApp === 'route'" />
  </div>
</template>

<script>
import Bus from "./components/bus/Bus.vue";
import Carriage from "./components/carriage/Carriage.vue";
import Client from "./components/client/Client.vue";
import Route from "./components/route/Route.vue";
import MainMenu from "./components/mainMenu.vue";

export default {
  name: "App",

  components: {
    Bus,
    Carriage,
    Client,
    Route,
    MainMenu,
  },
  data: function() {
    return {
      currentApp: "bus",
    };
  },

  methods: {
    getInfo: function(e) {
      this.currentApp = e;
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
