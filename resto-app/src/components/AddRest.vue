<template>
  <HeaderTag />
  <h1>Hello {{ name }}, welcome to Add Restaurant page</h1>
  <form class="add">
    <input
      type="text"
      name="name"
      placeholder="Enter name"
      v-model="restaurant.name"
    />
    <input
      type="text"
      name="contact"
      placeholder="Enter contact"
      v-model="restaurant.contact"
    />
    <input
      type="text"
      name="address"
      placeholder="Enter address"
      v-model="restaurant.address"
    />
    <button type="button" @click="addRestaurant">Add Restaurant</button>
  </form>
</template>

<script>
import HeaderTag from "./HeaderTag.vue";
import axios from "axios";
export default {
  name: "AddRest",
  data() {
    return {
      name: "",
      restaurant: {
        name: "",
        contact: "",
        address: "",
      },
    };
  },
  components: {
    HeaderTag,
  },
  methods: {
    async addRestaurant() {
      const result = await axios.post("http://localhost:3000/restaurants", {
        name: this.restaurant.name,
        contact: this.restaurant.contact,
        address: this.restaurant.address,
      });
      if (result.status == 201) {
        this.$router.push({ name: "HomePage" });
      }
    },
  },
  async mounted() {
    let user = localStorage.getItem("user-info");
    this.name = JSON.parse(user).name;
    if (!user) {
      this.$router.push({ name: "SignUp" });
    }
  },
};
</script>
