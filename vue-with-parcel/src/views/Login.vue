<template>
<div>
<section class="fdb-block">
  <div class="container">
    <div class="row justify-content-center">
      <div class="col-12 col-md-8 col-lg-7 col-xl-5 text-center">
        <div class="fdb-box">
          <div class="row">
            <div class="col">
              <h1>Log In</h1>
            </div>
          </div>
          <div class="row mt-4">
            <div class="col">
              <input type="text" class="form-control" placeholder="Email" v-model="email">
            </div>
          </div>
          <div class="row mt-4">
            <div class="col">
              <input type="password" class="form-control mb-1" placeholder="Password" v-model="password">
              <p class="text-right"><a v-on:click.prevent="registerForm" href="">Dont have an account?</a></p>
            </div>
          </div>
          <div class="row mt-4">
            <div class="col">
              <button class="btn btn-outline-secondary" type="button" v-on:click="login">Submit</button>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</section>
</div>
</template>

<script>
import axios from 'axios'
export default {
    data() {
        return {
            email: '',
            password: ''
        }
    },
    methods: {
        login() {
          Swal.showLoading()
            axios({
                url: "http://localhost:3000/user/login",
                method: "POST",
                data:{
                  email: this.email,
                  password: this.password
                }
            })
            .then(({data})=>{
              Swal.close()
              Swal.fire({
                icon: 'success',
                title: 'Success',
                text: 'User logged in!',
              })
                console.log(data)
                this.email = ""
                this.password = ""
            })
            .catch(err => {
              Swal.close()
              Swal.fire({
                icon: 'error',
                title: 'Oops...',
                text: `${err.response.data.message}`,
              })
                console.log(err.response.data)
            })
        },
        registerForm(){
            return this.$emit('registerForm')
        }
    }
}
</script>

<style>
.fdb-block{
    height: 100vh;
    background-image: url('../../img/bg-masthead.jpg')
}
</style>