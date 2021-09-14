<template>
  <div class="get">
    <p>GET:</p>
    <p>ID or Model</p>
    <input v-model="search" placeholder="ID or Model" />
    <p></p>
    <button @click="searchById">Search By ID</button>
    <button @click="searchByModel">Search By Model</button>
    <p></p>

    <table v-if="data.data">
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

    <p class="error" v-else>nothing found</p>
  </div>
</template>

<script>
import axios from "axios";
export default {
  name: "Get",
  data: function() {
    return {
      data: [],
      search: "",
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
    searchById: function() {
      try {
        axios
          .get(`http://localhost:8080/take/bus/${this.search}`)
          .then((response) => {
            (this.data.data = []), this.data.data.push(response.data);
          });
      } catch (e) {
        console.log(e);
      }
    },
    searchByModel: function() {
      try {
        axios
          .get(`http://localhost:8080/take/bus/model/${this.search}`)
          .then((response) => (this.data = response));
      } catch (e) {
        console.log(e);
      }
    },
  },
};
</script>

<style scoped>
a {
  margin: 1em;
  color: #42b983;
}
.error {
  color: red;
}
</style>
