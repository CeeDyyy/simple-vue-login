<template>
  <div class="home">
    <img alt="Vue logo" src="../assets/logo.png" />
    <HelloWorld :msg="'Welcome ' + username + ' to Your Vue.js App'" />
  </div>
</template>

<script>
// @ is an alias to /src
import HelloWorld from "@/components/HelloWorld.vue";

export default {
  name: "HomeView",
  components: {
    HelloWorld,
  },
  data() {
    return {
      username: "unknown",
    };
  },
  mounted() {
    let user = localStorage.getItem("user-info");
    if (user) {
      this.username = JSON.parse(user).username;
    }
  },
};
</script>
