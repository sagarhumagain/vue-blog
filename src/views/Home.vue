<template>
  <div class="home">
    <!-- <h1 ref="heading">My name is {{ name }} and my age is {{ age }}</h1> -->
      <h1 ref="heading" >My name is {{ name }} and my age is {{ age }}</h1>
      <button @click="age++">add a year on the age</button>
      <input v-model="name" type="text">
      <input v-model="age" type="text">


    <button @click="clickMe">Dont touch me</button>
  </div>
</template>

<script>
import { ref } from "@vue/reactivity";
// @ is an alias to /src
//composition api basics
export default {
  name: "Home",
  //function that execute first
  setup() {
    // let name = "sagar" //non reactive variables
    // let age = 26 

    //reactive values
    const name = ref('saggy')
    const age = ref(22)

    // return{name: name, age: age} (can be minimized as name and age because of same naming convention)

     const heading = ref(); //at this point refs does not have vale it is null of whatever you define
     // console.log(heading.value) //hello returned


    const clickMe = () => {
      name.value = "sagar"
      age.value = 26

      // console.log(heading, heading.value);
      // heading.value.textContent = "hello world";  //changing content of refs value else it will take value that included defaltly 
       heading.value.classList.add("changed"); //adding class to  from refs // click function is registered so it changes to value that used refs like heading and inner content 
    }

    return { name, age, clickMe , heading}; //returns data , functions, refs
  },

  created() {
    console.log("second");
  },

  mounted() {
    console.log("third");
  },
};
</script>
<style scoped>
.changed {
  color: rebeccapurple;
}
</style>
