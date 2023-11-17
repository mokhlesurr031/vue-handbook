<template>
  <h2 v-if="num==0">The number is zero</h2>
  <h2 v-else-if="num==5">The number is five</h2>
  <h2 v-else>The number is not zero</h2>

</template>

<script>
  export default{
    name: "App", 
    data(){
      return{
        num: 5,
      };
    },

  };
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

</style>
