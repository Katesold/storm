<template>
  <div class="containerLogin">
    <img alt="storm technologies logo" src=".././assets/StormLogo.png">
    <h1>Sign in to access the secret page</h1>
    <div class="loginDetails">
      <label for="username">
        <input id="username" type="text" v-model="username" >
      </label>
      <label for="password">
        <input id="password" type="password" v-bind:value= "password">
      </label>
      <p>You are logging in as {{ username }}</p>
      <button @click="postLogin">
        Login
      </button>
      <p>The credentials are not verified for the example purpose.</p>
    </div>
  </div>
</template>

<script>
const Cookie = process.client ? require('js-cookie') : undefined

export default {
  data() {
    return {
      username: 'StormTest',
      password: '-!NmmQR2pbmJSQ7'
    }
  },
  middleware: 'notAuthenticated',
  methods: {
    postLogin () {
      setTimeout(() => { // we simulate the async request with timeout.
        const auth = {
          accessToken: 'someStringGotFromApiServiceWithAjax'
        }
        this.$store.commit('setAuth', auth) // mutating to store for client rendering
        Cookie.set('auth', auth) // saving token in cookie for server rendering
        this.$router.push('/')
      }, 1000)
    }
  }
}
</script>

<style scoped>
.containerLogin{
    width: 300px;
    background: black;
    height: 420px;
    margin: 50px auto;
    border-radius: 10px;
    padding: 20px;
}
.containerLogin img{
    margin: auto;
    display: flex;
    align-self: center;
}
.containerLogin h1{
    font-size: 1.1em;
    padding: 30px 0 0;
    text-align: center;
}
.loginDetails{
    padding: 10px;
    text-align: center;
}
#username, #password{
    padding: 10px;
    margin: 5px;
    border-radius: 5px;
    border-color: black;
    width: 80%;
}
button{
    display: block;
    padding:0.35em 1.2em;
    border:0.1em solid #FFFFFF;
    background: #FFFFFF;
    margin: 10px auto;
    border-radius:0.12em;
    box-sizing: border-box;
    text-decoration:none;
    font-family:'Roboto',sans-serif;
    font-weight:300;
    color:black;
    text-align:center;
    transition: all 0.2s;
    cursor: pointer;
}
button:hover{
    background: #ff5858;
    border:0.1em solid #ff5858;
}
</style>
