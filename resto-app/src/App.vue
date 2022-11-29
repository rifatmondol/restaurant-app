<template>
  <router-view />
</template>

<script>
export default {
  name: "App",
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
body {
  padding: 0;
  margin: 0;
}
.logo {
  width: 100px;
}
.signup input,
.login input,
.add input {
  width: 320px;
  height: 40px;
  padding-left: 14px;
  border: 1px solid skyblue;
  display: block;
  margin: 0 auto;
  margin-bottom: 20px;
}
.signup button,
.login button,
.add button {
  width: 320px;
  height: 40px;
  border: 1px solid skyblue;
  background: skyblue;
  color: #fff;
  cursor: pointer;
}
</style>
