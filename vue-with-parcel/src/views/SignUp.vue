<template>
  <div class="register">
    <section class="fdb-block">
      <div class="container">
        <div class="row justify-content-center">
          <div class="col-12 col-md-8 col-lg-7 col-md-5 text-center">
            <div class="fdb-box fdb-touch">
              <div class="row">
                <div class="col">
                  <h1>Register</h1>
                </div>
              </div>
              <div class="row">
                <div class="col mt-4">
                  <input v-model="name" type="text" class="form-control" placeholder="Name">
                </div>
              </div>
              <div class="row mt-4">
                <div class="col">
                  <input v-model="email" type="text" class="form-control" placeholder="Email">
                </div>
              </div>
              <div class="row mt-4">
                <div class="col">
                  <input v-model="password" type="password" class="form-control mb-1" placeholder="Password">
                  <p class="text-right"><a v-on:click.prevent="loginForm" href="">Already have an account?</a></p>
                </div>
              </div>
              <div class="row mt-4">
                <div class="col">
                  <button class="btn btn-primary" type="button" v-on:click="register">Submit</button>
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
  data(){
    return{
      name: "",
      email: "",
      password: ""
    }
  },
  methods:{
    loginForm(){
      return this.$emit('loginForm')
    },
    register(){
      console.log('Masuk Register')
      Swal.showLoading()
      axios({
        url: "http://localhost:3000/user/register",
        method: "POST",
        data:{
          name: this.name,
          email: this.email,
          password: this.password
        }
      })
      .then(({data})=>{
        console.log(data)
        Swal.close()
        Swal.fire({
          icon: 'success',
          title: 'Success',
          text: 'User created!',
        })
        this.name = ""
        this.email = ""
        this.password = ""
      })
      .catch(err => {
        console.log(err)
        Swal.close()
        Swal.fire({
          icon: 'error',
          title: 'Oops...',
          text: `${err.response.data.message}`,
        })
      })
    }
  }
}
</script>

<style>

</style>