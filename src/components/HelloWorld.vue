<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <input v-model="name" placeholder="Enter Name" />
    <br />
    <input v-model="email" placeholder="Enter valid email" />
    <br />
    <input v-model="birthDate" placeholder="Enter birth date" />
    <br />
    <button v-on:click="main">Submit</button>
  </div>
</template>

<script>
export default {
  name: "HelloWorld",
  props: {
    msg: String,
    // name: String,
    // email: String,
    // birthDate: String
  },
  data: function () {
    return {
      name: "",
      email: "",
      birthDate: "",
      isValid: {
        name: false,
        email: false
        // birthDate: false,
      },
      isNameValid: false,
      isEmailValid: false
    };
  },
  methods: {
    main: function () {
      // console.log(this.changeValidStatus(this.isValidName, this.name))
      // const validName = this.changeValidStatus(this.isValidName, this.name)
      // this.valid.name = validName
      // this.isNameValid = true;
      // this.isEmailValid = true;

      this.isNameValid = this.changeValidStatus(this.isValidName, this.name)

      this.isEmailValid = this.changeValidStatus(this.isValidEmail, this.email)

      if(this.isEverythingValid()) {
        alert("shit worked")
      } else {
        alert("please fill everything before submitting")
      }


    
    },
    test: function() {
      console.log(this.isEverythingValid())
    },
    isEverythingValid: function() {
      const validInfo = [this.isNameValid, this.isEmailValid];

      for(let i = 0; i < validInfo.length; i++) {
        if(validInfo[i] == false) {
          return false
        }
      }

      return true;

      // console.log(validInfo.some((e) => {e = true;}))

      // bject.keys(isValidInfo).forEach(function (key) {
      //   console.log(key, isValidInfo[key]);
      // }) 



      // const isValidInfo = this.isValid

      // Object.keys(isValidInfo).forEach(function (key) {
      //   console.log(key, isValidInfo[key]);

      // }) 
    },
    changeValidStatus: function(test, element) {
      return test(element);
    },
    isValidName: function (name) {
      //returns true if string is filled, makes it so string filled with empty space returns false
      return /\S/.test(name);
    },
    isValidEmail: function (elementValue) {
      //got this from http://zparacha.com/validate-email-address-using-javascript-regular-expression
      var emailPattern = /^[a-zA-Z0-9._-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,4}$/;
      return emailPattern.test(elementValue);
    },
  },
};
//on submit chekc if name, email, birthdate are valid -
//if they all return true then and post do the post
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>
