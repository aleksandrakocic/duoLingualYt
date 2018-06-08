<template>
  <div id="app">
    <h1>YouTube</h1>




<router-view></router-view>



  </div>
</template>

<script>

export default {
  name: 'app',
  components: {

  }
}
</script>

<style lang="scss">


body{
   background: black;
   font-family: 'Poppins', sans-serif;
   #app {
        h1{
           color: red;
          text-align: center;
    }    
}}


</style>

