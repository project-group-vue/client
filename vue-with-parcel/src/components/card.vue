<template>
  <div>
    <div class="card mb-3">
      <img
        :src="picture.image"
        :img="picture.image"
        class="card-img-top"
        alt
        height="300"
        width="100"
      />
      <div class="card-body">
        <h5 class="card-title">Card title</h5>
        <p class="card-text">ini gambar</p>
        <p class="card-text">
          <small class="text-muted">Last updated 3 mins ago</small>
        </p>
        <a :href="shareFb" target="_blank">
          <img
            src="http://orangecountycustomwebsitedesign.com/wp-content/uploads/2017/02/facebook-share-button.png"
            alt
            height="40px"
            width="40px"
          />
        </a>
      </div>
    </div>
    <div class="line"></div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      img: "",
      shareFb: `http://www.facebook.com/sharer.php?u=${this.picture.image}`
    };
  },
  props: ["picture"]
};
</script>

<style>
.card-body img {
  cursor: pointer;
}
</style>