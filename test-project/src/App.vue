<template>
  <h2>{{ name }}</h2>
  <button v-on:click="name='Batman'">Click Me</button>

  <h2>{{count}}</h2>
  <div>
    <button v-on:click="increment">Increment</button>
    <button @click="decrement">Decrement</button>
  </div>

</template>

<script>
  export default{
    name: "App", 
    data(){
      return{
        name: "Mahin",
        count: 0
      };
    },
    methods: {
      increment(){
        this.count++
      },
      decrement(){
        this.count--
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
