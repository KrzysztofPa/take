<template>
  <div class="put">
    <p>PUT:</p>
    <p>ID</p>
    <input v-model="Id" placeholder="ID" />
    <p>FirstName</p>
    <input v-model="Model" placeholder="FirstName" />
    <p>LastName</p>
    <input v-model="Registration" placeholder="LastName" />

    <button @click="put">SEND</button>
    <p class="success" v-if="send">SUCCESS</p>
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
      send: false,
    };
  },
  methods: {
    put: function() {
      let bodyFormData = new FormData();
      bodyFormData.append("model", this.Model);
      bodyFormData.append("registration", this.Registration);

      var object = {};
      bodyFormData.forEach((value, key) => (object[key] = value));
      var json = JSON.stringify(object);

      axios({
        method: "put",
        url: `http://localhost:8080/take/client/${this.Id}`,
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

<style scoped></style>
