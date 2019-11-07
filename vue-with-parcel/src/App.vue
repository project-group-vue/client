<template>
  <div v-if="registerShow === false">
    <div class="container text-center my-auto masthead">
      <h1 class="mb-1">EDYIBPITSM</h1>
      <h3 class="mb-5">
        <em>Make Your Post Better</em>
      </h3>
      <a
        class="btn btn-primary btn-xl js-scroll-trigger"
        v-on:click="findMore"
        href="#about"
      >Find Out More</a>
    </div>
  </div>
</template>

<script>
import login from "./views/Login";
import signup from "./views/SignUp"
export default {
  components: {
    login, signup
  },
  data() {
    return {
      registerShow: false
    };
  },
  methods: {
    findMore() {
      this.registerShow = true;
    }
  }
};
</script>

<style>
body {
  background: url("../img/bg-masthead.jpg") no-repeat center center fixed;
  -webkit-background-size: cover;
  -moz-background-size: cover;
  background-size: cover;
  -o-background-size: cover;
}

.masthead {
  min-height: 30rem;
  position: relative;
  display: table;
  width: 100%;
  height: auto;
  padding-top: 8rem;
  padding-bottom: 8rem;
  background-position: center center;
  background-repeat: no-repeat;
  background-size: cover;
}

.masthead h1 {
  font-size: 4rem;
  margin: 0;
  padding: 0;
}
</style>

