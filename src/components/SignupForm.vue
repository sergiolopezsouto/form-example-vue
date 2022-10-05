<template>
  <form @submit.prevent="handleSubmit">

    <label> Email: </label>
    <input type="email" required v-model="email">

    <label> Password: </label>
    <input type="password" required v-model="password">
    <div class="error" v-if="passwordError"> {{passwordError}} </div>

    <label> Role: </label>
    <select v-model="role">
        <option value='designer'> Web Designer </option>
        <option value='developer'> Web Developer </option>
    </select>

    <input type="checkbox" required v-model="terms">
    <label> Accept terms and conditions. </label>

    <div class="submit">
        <button> Create an account </button>
    </div>

  </form>
</template>


<script>
import { handleError } from '@vue/runtime-core'
export default {
    data() {
        return{
            email: '' ,
            password: '' ,
            role: '' ,
            terms: false ,
            passwordError: '' ,
        }
    },
    methods: {
        handleSubmit() {
            // validate password
            if (this.password.length < 5) {
                    this.passwordError= 'Password must be at least 6 chars long'
            } else {
                this.passwordError=''
            }
        }
    }
}
</script>


<style>
form{
    max-width: 420px;
    margin: 30px auto;
    background: white;
    text-align: left;
    padding: 40px;
    border-radius: 10px;
}
label{
    color: #aaa;
    display: inline-block;
    margin: 25px 0 15px;
    font-size: 0.6em;
    text-transform: uppercase;
    letter-spacing: 1px;
    font-weight: bold;
}
input, select{
    display: block;
    padding: 10px 6px;
    width: 100%;
    box-sizing: border-box;
    border: none;
    border-bottom: 1px solid #ddd;
    color: #555;
}
input[type="checkbox"]{
    display: inline-block;
    width: 16px;
    margin: 0 10px 0 0;
    position: relative;
    top: 2px;
}
button {
    background-color: #0b6dff;
    border: 0;
    padding: 10px 20px;
    margin-top: 20px;
    color: white;
    border-radius: 20px;
}
.submit {
    text-align: center;
}
.error {
    color: #ff0062;
    margin-top: 10px;
    font-size: 0.8em;
    font-weight: bold;
}
</style>