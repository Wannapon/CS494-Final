<template>
  <div class="about">
    <div class="form-group">
      <label>Username</label>
      <input type="text" class="form-control" v-model="user.username">
    </div>
    <div class="form-group">
      <label>Mail</label>
      <input type="text" class="form-control" v-model="user.mail">
    </div>
    <button class="btn btn-primary" @click="submit">Submit</button>
  </div>
</template>
<script>
import axios from "axios";
export default {
  data() {
    return {
      user:{
        username:'',
        mail:''
      }
    };
  },
  methods:{
    submit() {
 let uri = "https://lab7-http.firebaseio.com/data.json";
 axios.post(uri, this.user).then(response => {
 console.log(response);
 });
 }
 } ,
  mounted() {
    axios({
      method: "GET",
      url: "http://jsonplaceholder.typicode.com/todos"
    }).then(result => {
      this.httpdata = result.data;
    });
  }
};
</script>