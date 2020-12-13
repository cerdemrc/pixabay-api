<template>
  <div class="form">
    <div class="input-group">
      <input
        type="text"
        class="form-control"
        v-model="description"
        placeholder="Search image"
      />
      <div class="input-group-append">
        <select class="custom-select" v-model="order">
          <option>popular</option>
          <option>latest</option>
        </select>
      </div>
    </div>
    <button @click="search" class="btn btn-outline-light btn-block">
      Search
    </button>
  </div>
</template>

<script>
import axios from "axios";
import { eventBus } from "../main";
export default {
  data() {
    return {
      images: "",
      description: "",
      order: "popular",
    };
  },
  methods: {
    search() {
      axios
        .get(
          "https://pixabay.com/api/?key=18882425-c251e5c9482a78e13dcc144c3&q=" +
            this.description +
            "&image_type=photo&per_page=100&order=" +
            this.order
        )
        .then((response) => {
          this.images = response.data.hits;
          eventBus.$emit("sendData", this.images);
        });
    },
  },
};
</script>

<style scoped lang="scss">
.form {
  display: inline;
  justify-content: center;
  width: 60%;

  .btn {
    margin-top: 20px;
  }
}
</style>