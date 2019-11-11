<template>
  <div class="hello">
    <div class="holder">
      <!-- <div
        v-bind:style="{backgroundColor: bgColor, width: bgWidth, height: bgHeight }"
        class="skills"
      >-->
      <!-- <div class="container"> -->
      <form @submit.prevent="addSkill">
        <input
          type="text"
          placeholder="Enther a skill you have.."
          v-model="skill"
          v-validate="'min:5'"
          name="skill"
        />

        <!-- <input type="checkbox" id="checkbox" v-model="checked" /> -->
        <transition
          name="alert-in"
          enter-active-class="animated flipInX"
          leave-active-class="animated flipOutX"
        >
          <!-- <p class="alert" v-if="errors.has('skill')">{{ errors.first('skill') }}</p> -->
        </transition>
      </form>
      <!-- </div> -->
      <!-- <h1 v-once>{{name}}</h1> -->

      <ul>
        <transition-group
          name="list"
          enter-active-class="animated bounceInUp"
          leave-active-class="animated bounceOutDown"
        >
          <li v-for="(data, index) in skills" :key="index">
            <!-- {{index}}.  -->
            {{data.skill}}
            <i class="fa fa-minus-circle" v-on:click="remove(index)"></i>
          </li>
        </transition-group>
      </ul>

      <!-- <p v-if="skills.length >= 1">THESE ARE THE SKILLS THAT YOU POSSESS</p> -->
      <!-- {{ btnState ? 'The button is diabled' : 'the button is active'}} -->
      <!-- <button v-on:click="changeName" v-bind:disabled="btnState">Change Name</button> -->
      <!-- </div> -->
    </div>
  </div>
</template>

<script>
export default {
  name: "skills",
  data() {
    return {
      skill: "",
      // checked: false,
      skills: [
        { skill: "vue.js" },
        { skill: "frontend engineer" }
        // btnState: true
      ]
      // alertObject: {
      //   alert: true
      // },
      // bgColor: "white",
      // bgWidth: "100%",
      // bgHeight: "100%"
    };
  },
  methods: {
    addSkill() {
      this.skills.push({ skill: this.skill });
      this.skill = "";
      // this.$validator.validateAll().then(result => {
      //   if (result) {
      //     // console.log("this checkbox valus is: " + this.checked);
      //   } else {
      //     // console.log("Not Valid");
      //   }
      // });
    },
    remove(id) {
      this.skills.splice(id, 1);
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
@import "https://cdn.jsdelivr.net/npm/animate.css@3.5.1";
@import "https://maxcdn.bootstrapcdn.com/font-awesome/4.7.0/css/font-awesome.min.css";

.holder {
  background: #fff;
}

ul {
  margin: 0;
  padding: 0;
  list-style-type: none;
}

ul li {
  padding: 20px;
  font-size: 1.3em;
  background-color: #e0edf4;
  border-left: 5px solid #3eb3f6;
  margin-bottom: 2px;
  color: #3e5252;
}

p {
  text-align: center;
  padding: 30px 0;
  color: gray;
}

.container {
  box-shadow: 0px 0px 40px lightgray;
}

.alert {
  background: #fdf2ce;
  font-weight: bold;
  display: inline-block;
  padding: 5px;
  margin-top: -20px;
}

input {
  width: calc(100% - 40px);
  border: 0;
  padding: 20px;
  font-size: 1.3em;
  background-color: #323333;
  color: #687f7f;
}

.alert-in-enter-active {
  animation: bounce-in 0.5s;
}
.alert-in-leave-active {
  animation: bounce-in 0.5s reverse;
}

@keyframes bounce-in {
  0% {
    transform: scale(0);
  }
  50% {
    transform: scale(1.5);
  }
  100% {
    transform: scale(1);
  }
}

.fa-minus-circle {
  float: right;
}
</style>
