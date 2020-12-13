<template>
  <div class="container mt-3">
    <h1>Free Images</h1>
    <hr />
    <h2>
      2.2 million images and reviews shared by our generous news were reviewed.
    </h2>
    <appForm />
    <appImage />
    <appBacktoTop>
      <button type="button" class="btn btn-info btn-to-top">
        <i class="fa fa-chevron-up"></i>
      </button>
    </appBacktoTop>
  </div>
</template>

<script>
import Form from "./components/Form";
import Image from "./components/Image";
import BackToTop from "vue-backtotop";
export default {
  components: {
    appForm: Form,
    appImage: Image,
    appBacktoTop: BackToTop,
  },
};
</script>

<style scoped lang="scss">
$white: white;

@mixin share {
  text-align: center;
  color: $white;
  margin: 20px;
}

.container {
  max-width: 1200px;
}

h1 {
  @include share;
  font-size: 3rem;
  font-family: "Major Mono Display", monospace;
  letter-spacing: 10px;
}
h2 {
  @include share;
  font-family: "Bubbler One", sans-serif;
  font-size: 1rem;
  letter-spacing: 3px;
}
.btn {
  width: 50px;
  height: 50px;
  border-radius: 40px;

  & .fa {
    font-size: 1.5rem;
  }
}
</style>
