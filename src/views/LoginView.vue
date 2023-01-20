<template>
  <div class="login">
    <h1>Login</h1>
    <div class="form-control">
      <label for="username">Username</label>
      <input type="text" name="username" v-model.trim="username" placeholder="Username" />
    </div>
    <div class="form-control">
      <label for="password">Password</label>
      <input type="password" name="password" v-model.trim="password" placeholder="Password" />
    </div>
    <button type="button" @click="login()">Login</button>
  </div>
</template>

<script>
import axios from 'axios';
export default {
  name: "LoginView",
  data() {
    return {
      username: "",
      password: "",
    };
  },
  methods: {
    async login() {
      if (this.username != "" && this.password != "") {
        let result = await axios.get(
          `http://localhost:3000/users?username=${this.username}&password=${this.password}`
        );
        if(result.status == 200 && result.data.length > 0) {
          localStorage.setItem("user-info", JSON.stringify(result.data[0]))
          this.$router.push({name: 'home'})
        }
      } else {
        console.log("please enter username and password");
      }
    },
  },
  mounted() {
      let user = localStorage.getItem('user-info');
      if(user) {
        this.$router.push({name: 'home'})
      }
    }
};
</script>

<style scoped>
.form-control {
  padding-bottom: 10px;
}
.form-control label {
  padding-right: 10px;
}
</style>