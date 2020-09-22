<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <input v-model="name" placeholder="Enter Name" />
    <br />
    <input v-model="email" placeholder="Enter valid email" />
    <br />
    <br />
    <p>Enter valid birth date</p>
    <input type="date" v-model="birthDate" />
    <br />
    <p v-if="isChecked">I agree to be contacted via email</p>
    <p v-else>I don't agree to be contacted via email</p>
    <input type="checkbox" id="checkbox" v-model="isChecked" />
    <br />
    <br />
    <button v-on:click="main">Submit</button>
    <button v-on:click="clearEverything">clear</button>
  </div>
</template>

<script>
export default {
  name: "HelloWorld",
  props: {
    msg: String,
  },
  data: function () {
    return {
      name: "",
      email: "",
      birthDate: "",
      isNameValid: false,
      isEmailValid: false,
      isChecked: false,
    };
  },
  watch: {
    name() {
      this.isNameValid = this.changeValidStatus(this.isValidName, this.name);
    },
    email() {
      this.isEmailValid = this.changeValidStatus(this.isValidEmail, this.email);
    },
    birthDate() {
      //check if valid birthdate
      //change valid status of birthdateS
      console.log("do stuff");
      //
    },
  },
    methods: {
      main: function () {
        //needs birthdate 
        if (
          this.isEverythingValid([
            this.isNameValid,
            this.isEmailValid,
            this.isChecked,
          ])
        ) {
          //do http post stuff
          alert("shit worked");
        } else {
          alert(
            "please fill everything before submitting, dont forget to agree to be contacted. Date of birth can be left blank."
          );
        }
      },
      isEverythingValid: function (arr) {
        const isTrue = (e) => (e ? true : false);

        return arr.every(isTrue);
      },
      changeValidStatus: function (test, element) {
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
      clearEverything: function () {
        this.name = "";
        this.email = "";
        this.birthDate = "";
        this.isChecked = false;
      },
    },
  }
</script>
<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>


<!-- 
what it needs 
---1. user name - cannot be blank 
---2. email - cannot be nlank and must be a valid email address
3. birth date - can be blank
             if not empty, the input must be a valid date
---4. check box - afreement ot be contacted - MUST BE CHECKKED

---5. submit button is disabl;e if anay of the previous fields are invalid
---6. form has a clear button that clears the rest of the of the form
7. to submit he from, make an http post request to 
 const httpPostRequest = https://my-json-server.typicode.com/JustUtahCoders/interview-users-api/users 
-->

<!--
this might work for birth date stuff
got it from https://stackoverflow.com/questions/32378590/set-date-input-fields-max-date-to-today

<input id="datefield" type='date' min='1899-01-01' max='2000-13-13'></input>

var today = new Date();
var dd = today.getDate();
var mm = today.getMonth()+1; //January is 0!
var yyyy = today.getFullYear();
 if(dd<10){
        dd='0'+dd
    } 
    if(mm<10){
        mm='0'+mm
    } 

today = yyyy+'-'+mm+'-'+dd;
document.

 -->