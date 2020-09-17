<template>
  <div id="app">
    <HelloWorld msg="Contact Us"/>
  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'

export default {
  name: 'App',
  components: {
    HelloWorld
  }
}
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

<!-- 
what it needs 
1. user name - cannot be blank
2. email - cannot be nlank and must be a valid email address
3. birth date - can be blank
             if not empty, the input must be a valid date
4. check box - afreement ot be contacted - MUST BE CHECKKED

5. submit button is disabl;e if anay of the previous fields are invalid
6. form has a clear button that clears the rest of the of the form
7. to submit he from, make an http post request to 
 const httpPostRequest = https://my-json-server.typicode.com/JustUtahCoders/interview-users-api/users 
-->

