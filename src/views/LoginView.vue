<template>
  <div class="login">
    <h1>Login</h1>
    <form @submit.prevent="loginSubmit">
      <div class="form-control">
        <label for="username">Username</label>
        <input type="text" name="username" placeholder="Username" />
      </div>
      <div class="form-control">
        <label for="password">Password</label>
        <input type="password" name="password" placeholder="Password" />
      </div>
      <button type="submit">Login</button>
    </form>
  </div>
</template>

<script>
export default {
  name: "LoginView",
  data() {
    return {
      input: {
        username: "",
        password: "",
      },
    };
  },
  methods: {
    loginSubmit(loginEvent) {
      if (
        loginEvent.target.elements.username.value != "" &&
        loginEvent.target.elements.password.value != ""
      ) {
        this.username = loginEvent.target.elements.username.value;
        this.password = loginEvent.target.elements.password.value;
        console.log("login");
      } else {
        console.log("please enter username and password");
      }
    },
  },
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