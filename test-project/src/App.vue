<template>
  <div>{{firstName}} {{lastName}}</div>
  <div>Computed Fullname- {{fullName}}</div>

</template>

<script>
  export default{
    name: "App", 
    data(){
      return{
        firstName: "jeffy",
        lastName: "mahin"
      };
    },
    methods: {
    },
    computed:{
      fullName(){
        return `${this.firstName} ${this.lastName}`
      }
    }
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
