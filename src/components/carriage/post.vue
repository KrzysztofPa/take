<template>
  <div class="post">
    <p>POST:</p>
    <p>StartTime</p>
    <input v-model="Model" placeholder="StartTIme" />
    <p>endTime</p>
    <input v-model="Registration" placeholder="endTime" />
    <p>routeID</p>
    <input v-model.number="Seats" placeholder="routeID" />
    <p>busID</p>
    <input v-model.number="busID" placeholder="busID" />
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
      Id: 0,
      Model: "",
      Registration: "",
      Seats: 0,
      busID: 0,
      send: false,
    };
  },
  methods: {
    post: async function() {
      let myJSON = `{"startTime": "${this.Model}",
      "endTime":" ${this.Registration}",
      "route" :{
        "id" :"${this.Seats}"
      },
      "bus":{
        "id": "${this.busID}"
      }
      }`;

      await axios({
        method: "post",
        url: "http://localhost:8080/take/carriage",
        data: JSON.parse(myJSON),
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
