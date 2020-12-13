<template>
  <div class="container">
    <div class="row row-cols-md-3 mt-5">
      <div class="col mb-4" v-for="image in imageList" :key="image.id">
        <div class="image">
          <img :src="image.webformatURL" />
          <div class="info">
            <h6>@{{ image.user }}</h6>
            <p>
              <i class="fa fa-heart" aria-hidden="true"></i> {{ image.likes }}
            </p>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import { eventBus } from "../main";
export default {
  data() {
    return {
      imageList: "",
    };
  },
  created() {
    eventBus.$on("sendData", (images) => {
      this.imageList = images;
    });
  },
};
</script>

<style scoped lang="scss">
$white: white;
$black: black;

p {
  color: $white;
  margin-top: -70px;
  margin-left: 280px;
}
h6 {
  margin-top: 5px;
}

img {
  width: 350px;
  height: 250px;
  display: flex;
  border-radius: 10px;
  transition: 0.4s ease-out;

  &:hover {
    opacity: 0.8;
    box-shadow: 0px 7px 10px $black;
  }
}
</style>