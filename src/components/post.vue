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
    };
  },
  methods: {
    post: function() {
      let bodyFormData = new FormData();
      bodyFormData.append("Model", this.Model);
      bodyFormData.append("Registration", this.Registration);
      bodyFormData.append("Seats", this.Seats);
      console.log(bodyFormData);

      try {
        axios
          .post("http://localhost:8080/take/bus")
          .data(bodyFormData)
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
