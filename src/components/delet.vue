<template>
  <div class="delete">
    <p>DELETE:</p>
    <p>ID</p>
    <input v-model.number="id" placeholder="ID" />
    <p></p>
    <button @click="delet">Delete</button>
  </div>
</template>

<script>
import axios from "axios";
export default {
  name: "Delet",
  data: function() {
    return {
      response: "",
      id: 0,
    };
  },
  methods: {
    delet: function() {
      try {
        axios
          .delete(`http://localhost:8080/take/bus/${this.id}`)
          .then((response) => (this.response = response));
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
