<template>
  <Today></Today>
  <SixDays></SixDays>
</template>

<script>
  import Today from '@/components/Today.vue'
  import SixDays from '@/components/SixDays.vue'

  export default {
    name: 'App',
    components: {
      Today,
      SixDays
    },


  }
</script>

<style>
  body{
    margin: 0;
    padding: 0;
    -webkit-box-sizing: border-box;
    box-sizing: border-box;
    font-family: sans-serif;
  }

  *
  *:before,
  *:after{
    margin: 0;
    padding: 0;
    -webkit-box-sizing: border-box;
    box-sizing: border-box;
  }

  img{
    width: 100px;
  }

  #app {
    width: 100%;
   max-width: 900px;
   border-radius: 20px;
   margin: 0 auto;
   overflow: hidden;
   -webkit-box-shadow: 5px 5px 15px 4px #6b6b6b;
   box-shadow: 5px 5px 15px 4px #6b6b6b;
  }
</style>
