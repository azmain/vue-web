<template>
  <div id="app">
    <Navbar></Navbar>
    <div class="container">
      <router-view></router-view>
    </div>
  </div>
</template>
<script>
import Navbar from '@/components/Navbar'
export default {
  name: "app",
  components: {
    Navbar
  }
}
</script>

<style>
* {
  font-family: 'Poppins', sans-serif,
}

body{
  background-color: #676768;
}
</style>
