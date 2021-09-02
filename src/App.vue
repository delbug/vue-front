<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png" />
    <ul>
      <li v-for="(item, i) in users" :key="i">
        <div>名字{{ item.name }}</div>
        <div>邮箱{{ item.email }}</div>
      </li>
    </ul>
  </div>
</template>

<script>
import axios from "axios";

export default {
  name: "App",
  data() {
    return {
      users: [],
    };
  },
  mounted() {
    axios.get("http://localhost:3000/api/users").then((res) => {
      console.log("res", res);

      this.users = res.data;
    });
  },
};
</script>

<style>
li {
  list-style: none;
  border: 1px solid skyblue;
}
</style>
