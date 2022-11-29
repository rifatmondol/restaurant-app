<template>
  <HeaderTag />
  <h1>Hello {{ name }}, welcome to home page</h1>
  <table border="1">
    <tr>
      <th>Id</th>
      <th>Name</th>
      <th>Contact</th>
      <th>Address</th>
      <th>Action</th>
    </tr>
    <tr v-for="item in restaurant" :key="item.id">
      <td>{{ item.id }}</td>
      <td>{{ item.name }}</td>
      <td>{{ item.contact }}</td>
      <td>{{ item.address }}</td>
      <td>
        <router-link :to="'/update-rest/' + item.id">Update</router-link>
        <button @click="deleteRestaurant(item.id)">Delete</button>
      </td>
    </tr>
  </table>
</template>

<script>
import HeaderTag from "./HeaderTag.vue";
import axios from "axios";
export default {
  name: "HomePage",
  data() {
    return {
      name: "",
      restaurant: [],
    };
  },
  components: {
    HeaderTag,
  },
  methods: {
    async deleteRestaurant(id) {
      let result = await axios.delete(
        "http://localhost:3000/restaurants/" + id
      );
      if (result.status == 200) {
        this.loadData();
      }
    },
    async loadData() {
      let user = localStorage.getItem("user-info");
      this.name = JSON.parse(user).name;
      if (!user) {
        this.$router.push({ name: "SignUp" });
      }
      let result = await axios.get("http://localhost:3000/restaurants");
      this.restaurant = result.data;
    },
  },
  async mounted() {
    this.loadData();
  },
};
</script>

<style>
table {
  margin: 0 auto;
  border-collapse: collapse;
}
th,
td {
  width: 200px;
  height: 40px;
}
</style>

