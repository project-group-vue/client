<template>
  <div>
    <div>
      <transition name="fade">
        <div v-if="loginShow === false && registerShow === false && !isLogin">
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
      </transition>
      <transition name="fade">
        <login
          v-if="loginShow === true && !isLogin"
          @registerForm="registerForm"
          @loginEvent="loginEvent"
        ></login>
      </transition>
      <transition name="fade">
        <signup v-if="registerShow === true && !isLogin" @loginForm="loginForm"></signup>
      </transition>
    </div>
    <mainPage
      v-if="loginShow === false && registerShow === false && isLogin"
      @logoutEvent="logoutEvent"
    ></mainPage>
  </div>
</template>

<script>
import login from "./views/Login";
import signup from "./views/SignUp";
import mainPage from "./views/MainPage";
export default {
  components: {
    login,
    signup,
    mainPage
  },
  data() {
    return {
      isLogin: null,
      loginShow: false,
      registerShow: false
    };
  },
  methods: {
    findMore() {
      this.loginShow = true;
    },
    registerForm() {
      this.registerShow = true;
      this.loginShow = false;
    },
    loginForm() {
      this.registerShow = false;
      this.loginShow = true;
    },
    loginEvent() {
      this.registerShow = false;
      this.loginShow = false;
      this.isLogin = localStorage.getItem("token");
    },
    logoutEvent() {
      this.isLogin = null;
    }
  },
  created() {
    if (localStorage.getItem("token")) {
      this.isLogin = localStorage.getItem("token");
      this.registerShow = false;
      this.loginShow = false;
    } else {
      this.isLogin = null;
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

.fade-enter-active {
  transition: opacity 1s ease-in;
}
.fade-enter/* .fade-leave-active below version 2.1.8 */ {
  opacity: 0;
}
</style>

