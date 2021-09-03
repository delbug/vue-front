<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png" />
    <ul>
      <li v-for="(item, i) in users" :key="i">
        <div>名字：{{ item.name }}</div>
        <div>邮箱：{{ item.email }}</div>
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
  // 1 2
  mounted() {
    let url = "http://120.26.81.60:3000/api/users";
    // let url = "/api/users";
    console.log("url---:", url);
    axios.get(url).then((res) => {
      console.log("res", res);
      this.users = res.data;
    });
  },
};
</script>

<style>
#app {
  width: 100%;
  text-align: center;
}

img {
  margin: 0 auto;
}

li {
  list-style: none;
  border: 1px solid skyblue;
  padding: 20px;
  text-align: left;
  background-color: #ccc;
}
</style>
