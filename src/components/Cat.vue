<template>
  <div class="cat">
      <img  :src="imageUrl"  height="300" width="400" style="border: 8px solid black;"  >
  </div>
</template>
<script>
import axios from 'axios'
export default {
  data() {
    return {imageUrl: String};
  },
  /*created() {
      this.loadNextImage();
  },*/
  methods: {
    async loadNextImage() {
      try {
        axios.defaults.headers.common["x-api-key"] = "8b51ae3c-5ef7-4702-b2d2-af53ad86feb1"; 

        let response = await axios.get(
          "https://api.thecatapi.com/v1/images/search",
          { params: { limit: 1, size: "full" } }
        ); // Ask for 1 Image, at full resolution

        this.imageUrl = response.data[0].url; // the response is an Array, so just use the first item as the Image

        console.log("url:", this.imageUrl);
      } catch (err) {
        console.log(err);
      }
    },
  },
};
</script>

<style>
.timer {
  display: flex;
  flex-direction: column;
}

.buttons {
  display: flex;
  justify-content: center;
}
</style>