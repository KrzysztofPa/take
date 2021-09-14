<template>
  <div id="app">
    <Menu />
    <p>GET:</p>
    <table>
      <tr>
        <th>ID</th>
        <th>Model</th>
        <th>Registration</th>
        <th>Seats</th>
      </tr>
      <tr v-for="dat in data.data" :key="dat.id">
        <th>{{ dat.id }}</th>
        <th>{{ dat.model }}</th>
        <th>{{ dat.registration }}</th>
        <th>{{ dat.seats }}</th>
      </tr>
    </table>
  </div>
</template>

<script>
import Menu from "./components/Menu.vue";
import axios from "axios";
export default {
  name: "App",

  components: {
    Menu,
  },
  data: function() {
    return {
      data: [],
    };
  },
  mounted() {
    try {
      axios
        .get("http://localhost:8080/take/bus/model/Fiat")
        .then((response) => (this.data = response));
    } catch (e) {
      console.log(e);
    }
  },
  methods: {
    getTags: function() {},
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
</style>
