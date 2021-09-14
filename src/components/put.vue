<template>
  <div class="put">
    <p>PUT:</p>
    <p>id</p>
    <input v-model="Id" placeholder="ID" />
    <p>Model</p>
    <input v-model="Model" placeholder="Model" />
    <p>Registration</p>
    <input v-model="Registration" placeholder="Registration" />
    <p>Seats</p>
    <input v-model.number="Seats" placeholder="Seats" />
    <p></p>
    <button @click="put">SEND</button>
  </div>
</template>

<script>
import axios from "axios";
export default {
  name: "Put",
  data: function() {
    return {
      Id: 0,
      Model: "",
      Registration: "",
      Seats: 0,
    };
  },
  methods: {
    put: function() {
      try {
        axios
          .get("http://localhost:8080/take/bus/model/Fiat")
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
</style>
