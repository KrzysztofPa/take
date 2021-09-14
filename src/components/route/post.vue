<template>
  <div class="post">
    <p>POST:</p>

    <p>Model</p>
    <input v-model="Model" placeholder="Model" />
    <p>Registration</p>
    <input v-model="Registration" placeholder="Registration" />
    <p>Seats</p>
    <input v-model.number="Seats" placeholder="Seats" />
    <p></p>
    <button @click="post">SEND</button>
    <p class="success" v-if="send">SUCCESS</p>
  </div>
</template>

<script>
import axios from "axios";
export default {
  name: "Post",
  data: function() {
    return {
      Model: "",
      Registration: "",
      Seats: 0,
      send: false,
    };
  },
  methods: {
    post: async function() {
      let bodyFormData = new FormData();
      bodyFormData.append("model", this.Model);
      bodyFormData.append("registration", this.Registration);
      bodyFormData.append("seats", this.Seats);

      var object = {};
      bodyFormData.forEach((value, key) => (object[key] = value));
      var json = JSON.stringify(object);

      await axios({
        method: "post",
        url: "http://localhost:8080/take/bus",
        data: json,
        headers: { "Content-Type": "application/json" },
      })
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
