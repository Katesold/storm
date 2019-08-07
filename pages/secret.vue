<template>
  <div class="secretTitle">
    <h1>This is a secret page.</h1>
    <NuxtLink to="/">
      Back home
    </NuxtLink>
    <Employees></Employees>

  </div>
</template>

<script>
import Employees from '.././components/Employees';
export default {
  components: {
    Employees
  },
  middleware: 'authenticated'
}
</script>

<style scoped>
.secretTitle{
  text-align: center;
  margin-top: 10px;
}

.secretTitle h1{
  padding: 10px;
}

.secretTitle a{
  padding: 3px;
}

.secretTitle a:hover{
  color: #1a202c;
  background: #ffffffcf;
  transition: all 0.8s;
  border-radius: 3px;
}

a{
  color: #FFF;
}

</style>

