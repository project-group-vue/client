<template>
<div>
  <mainPage></mainPage>
  <div>
    <transition name="fade">
      <login v-if="loginShow === true" @registerForm="registerForm"></login>
    </transition>
    <transition name="fade">
      <signup v-if="registerShow === true" @loginForm="loginForm"></signup>
    </transition>
  </div>
</div>
</template>

<script>
import login from "./views/Login";
import signup from "./views/SignUp";
import mainPage from "./views/MainPage"
export default {
  components: {
    login, signup,
    mainPage
  },
  data() {
    return {
      loginShow: false,
      registerShow: false
    };
  },
  methods: {
    findMore() {
      this.loginShow = true;
    },
    registerForm(){
      this.registerShow = true
      this.loginShow = false
    },
    loginForm(){
      this.registerShow = false
      this.loginShow = true
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

.fade-enter-active{
  transition: opacity 1.0s ease-in;
}
.fade-enter/* .fade-leave-active below version 2.1.8 */ {
  opacity: 0;
}
</style>

