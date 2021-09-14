<template>
  <div class="get">
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
import axios from "axios";
export default {
  name: "Get",
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
  methods: {},
};
</script>

<style scoped>
a {
  margin: 1em;
  color: #42b983;
}
</style>
