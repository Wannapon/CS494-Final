<template>
  <ul class="list-group">
    <li class="list-group-item" v-for="(u,index) in users" :key="index">{{u.username}} - {{u.mail}}</li>
  </ul>
</template>

<script>
  import axios from "axios";
export default {
  data() {
    return {
      users: []
    };
  },
  mounted() {
    axios
      .get("https://lab7-http.firebaseio.com/data.json")
      .then(response => {
        console.log(response);
        const data = response.data;
        for (let key in data) {
          const user = data[key];
          user.id = key;
          this.users.push(user);
        }
      })
      .catch(error => {
        console.log(error);
      });
  }
};
</script>

<style>
</style>
