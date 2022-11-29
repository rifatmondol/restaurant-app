<template>
  <div class="nav">
    <router-link to="/">Home</router-link>
    <router-link to="/add-rest">Add Restaurant</router-link>
    <!-- <router-link to="/update-rest">Update Restaurant</router-link> -->
    <a href="" @click="logout">Logout</a>
  </div>
</template>

<script>
export default {
  name: "HeaderTag",
  methods: {
    logout() {
      localStorage.clear();
      this.$router.push({ name: "LoginPage" });
    },
  },
};
</script>

<style>
.nav {
  background: #333;
  overflow: hidden;
  text-align: right;
}

.nav a {
  color: #fff;
  text-decoration: none;
  padding: 14px 16px;
  display: inline-block;
  font-size: 17px;
  margin-left: 5px;
}
.nav a:hover {
  background: #ddd;
  color: #000;
}
</style>