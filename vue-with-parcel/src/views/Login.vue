<template>
<div>


  <form>      
  <h2>Register</h2>

  Username:<br>
  <input type="text">
  <br>
  Password:<br>
  <input type="text">
  <br><br>
  <input type="submit" value="Submit">
</form>

    <button>Register</button>
</div>
</template>

<script>
import axios from 'axios'
export default {
    data() {
        return {
            username: '',
            password: ''
        }
    },
    methods: {
        login() {
            console.log(this.username)
            console.log(this.password)
        },
    }
}
</script>

<style>

</style>