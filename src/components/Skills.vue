<template>
  <div class="hello">  
    <h1>{{ msg }}</h1>
      <form @submit.prevent="addSkill">
      <input type=text placeholder="Enter a skill you have" v-model="skill" v-validate="'min:5'" name="skill">
      <transition name="alert-in" enter-active-class="animated fadeInDown" leave-active-class="animated fadeOutDown">
      <p class="alert" v-if="errors.has('skill')"> {{ errors.first('skill') }} </p>
      </transition>
      </form>
      <ul>
        <transition-group name="list" enter-active-class="animated fadeInUp" leave-active-class="animated fadeOutDown">
        <li v-for="(data, index) in skills" :key="index">{{index}}.{{data.skill}}   <i class="fa fa-minus-circle" v-on:click="remove(index)"></i></li>        
        </transition-group>
      </ul>
      <p v-if="skills.length > 1"> You have more than one skill</p>
      <p v-else>You have 0 or 1 skills</p>
      <div v-bind:style="{backgroundColor : bgColor, width : bgWidth, height : bgHeight}">Hello World</div>
  </div>
    

</template>

<script>
export default {
//  name : 'Skills', 
  props: {
    msg: String
  },
  data() {
    return {
      skill : '',
      skills : [
        {'skill' : 'Violin'},
        {'skill' : 'Piano'}
      ],
      bgColor : 'yellow',
      bgWidth : '100%',
      bgHeight : '30px'
    }
  },
  methods : {
    addSkill() {
      this.$validator.validateAll().then((result)=> {
        if (result) {
          this.skills.push({'skill' : this.skill})
          this.skill = ''
        } else {
          //console.log ("Not valid");
        }
      }
      )
    },
    remove(id) {
      this.skills.splice(id,1);
    }
  }
}
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
  background-color: #E0EDF4;
  border-left: 5px solid #3EB3F6;
  margin-bottom: 2px;
  color: #355252;
}

.alert {
  background-color :  yellow;
  width : 100%;
  height : 30 px;
}
.another {
  border : 5px solid black;
}

.alert-in-enter-active {
  animation: bounce-in .5s;
}

.alert-in-leave-active {
  animation: bounce-in .5s reverse;
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

i {
  float: right;
}
</style>
