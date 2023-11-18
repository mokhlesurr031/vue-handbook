<template>
  <h2>Form Handling</h2>
  <div>
    <pre>
      {{ JSON.stringify(formValues, null, 2) }}
    </pre>
  </div>

  <form @submit="submitForm">
    <div>
      <label for="name">Name: </label>
      <input type="text" id="name" v-model.trim="formValues.name">
    </div>


    <div>
      <label for="country">Country: </label>
      <select name="" id="country" v-model="formValues.country">
        <option value="">Select a country</option>
        <option value="india">India</option>
        <option value="bangladesh">Bangladesh</option>
      </select>
    </div>

    <div>
      <label for="job-location">Job Location: </label>
      <select name="" id="job-location" multiple v-model="formValues.jobLocation">
        <option value="india">India</option>
        <option value="bangladesh">Bangladesh</option>
        <option value="usa">USA</option>
      </select>
    </div>
    
    <div>
      <input type="checkbox" id="remoteWork" v-model="formValues.remoteWork" true-value="yes" false-value="no">
      <label for="remoteWork">Remote Work?: </label>
    </div>
    

    <div>
      <label>Skill Sets: </label>

      <input type="checkbox" id="html" value="html" v-model="formValues.skillSet">
      <label for="html">HTML</label>

      <input type="checkbox" id="css" value="css" v-model="formValues.skillSet">
      <label for="css">CSS</label>

      <input type="checkbox" id="js" value="js" v-model="formValues.skillSet">
      <label for="js">Javascript</label>
    </div>

    <div>
      <label>Experience: </label>
      <input type="radio" id="0-2" value="0-2" v-model="formValues.yearsOfExperience"/>
      <label for="0-2">0-2</label>

      <input type="radio" id="2-5" value="2-5" v-model="formValues.yearsOfExperience"/>
      <label for="2-5">2-5</label>
    </div>

    <div>
      <label for="age">Age: </label>
      <input type="number" id="age" v-model.number="formValues.age">
    </div>

    <div>
      <button>Submit</button>
    </div>


  </form>
</template>

<script>
  export default{
    name: "App", 
    data(){
      return{
        formValues: {
          name: '',
          country: '',
          jobLocation: [],
          remoteWork: "no",
          skillSet: [],
          yearsOfExperience: "",
          age: null

        }
      };
    },
    methods: {
      submitForm(event){
        event.preventDefault()
        console.log("form Values: ", this.formValues)
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
