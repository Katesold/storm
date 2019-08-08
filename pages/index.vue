<template>
  <div class="app">
    <Header></Header>
    <div class="auth" v-if="$store.state.auth">
      <p>
        You are authenticated. You can see the
        <NuxtLink to="/secret">
          secret page
        </NuxtLink>!
      </p>
      <button @click="logout">
        Logout
      </button>
    </div>
    <p id="loginText" v-else>
      Please
      <NuxtLink to="/login">
        login
      </NuxtLink>
    </p>
    <Footer></Footer>
  </div>
</template>

<script>
import Header from '.././components/Header';
import Footer from '.././components/Footer';
const Cookie = process.client ? require('js-cookie') : undefined

export default {
  components: {
    Header,
    Footer
  },
  methods: {
    logout () {
      Cookie.remove('auth')
      this.$store.commit('setAuth', null)
    }
  }
}
</script>
<style>
@import '.././css/reset.css';
@import '.././css/style.css';
@import url('https://fonts.googleapis.com/css?family=Roboto:400,700&display=swap');
body{
  color: #FFF;
  font-family: 'Roboto', sans-serif;
}
.app h1, .app a{
  color: #FFF;
}
#loginText{
  font-size: 1.5em;
  text-align: center;
  padding-top: 80px;
}
#loginText a{
  padding: 3px;
}

#loginText a:hover{
  color: #1a202c;
  background: #ffffffcf;
  transition: all 0.8s;
  border-radius: 3px;
}
.auth{
  text-align: center;
  padding-top: 50px;
}

.auth button{
  margin-top: 20px;
}

</style>
