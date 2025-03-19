<template>
  <div>
    <h1>{{ message }}</h1>
    <button @click="fetchData">fetch data from server</button>
  </div>
</template>

<script>
import axios from "axios";

export default {
  data() {
    return {
      message: "loading...",
    };
  },
  methods: {
    async fetchData() {
      try {
        const response = await axios.get("http://localhost:8000/data");
        this.message = response.data.message;
      } catch (error) {
        console.log("error:", error);
        this.message = "failed to fetch data from server";
      }
    },
  },
};
</script>
