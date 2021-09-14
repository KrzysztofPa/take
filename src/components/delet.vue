<template>
  <div class="delete">
    <p>DELETE:</p>
    <p>ID</p>
    <input v-model.number="id" placeholder="ID" />
    <p></p>
    <button @click="delet">Delete</button>
    <p class="success" v-if="send">SUCCESS</p>
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
      send: false,
    };
  },
  methods: {
    delet: function() {
      axios
        .delete(`http://localhost:8080/take/bus/${this.id}`)
        .then((response) => {
          //handle success
          if (response.status === 200) {
            this.send = true;
          }
        })
        .catch((response) => {
          this.send = false;
          //handle error
          console.log(response);
        });
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
