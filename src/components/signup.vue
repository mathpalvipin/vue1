<template>

	<div class="form">
		<input type="email" class="input" v-model="store.email" />
		
		 <input v-if="showPassword" type="text" class="input" v-model="store.password" />
           <input v-else type="password" class="input" v-model="store.password">

            
 
 <div class="eye" @click="toggleShow">
            	  <img v-if="!showPassword" :src="show">
            	  <img v-else :src="hide">
         

  </div>
        
		<label for="cars">Choose a color:</label>

<select name="cars" id="color" class="input" v-model='store.color' v-bind:style="{backgroundColor: store.color.c}" >
	

   <option v-for="color in colors" v-bind:value="color" v-bind:style="{backgroundColor:color.c}" >
       {{ color.name }}

    </option>
  
</select>
<div  v-if ="currentcolor" :style="{backgroundColor:currentcolor}"></div>
		<div class="button-group">
			<router-link class="myButton1" to="/login"
				>already registered !</router-link
			>

			<a href="#" class="myButton" @click="signup()">signup</a>
		</div>
	</div>
</template>
<script type="text/javascript">
	import { store } from "../store.js";
 import axios from 'axios';
import show from '../assets/eye-slash-solid.svg'
import hide from '../assets/eye-solid.svg'
export default {
	data() {
		return { store,
		  showPassword: true, 
		  show,
		  hide,
		  colors: [
        {'c':"#00FFFF", 'name':"Aqua"},
        {'c':"#0000FF", 'name':"Blue"},
        {'c':"#A52A2A", 'name':"Brown"},
        {'c':"#000000", 'name':"Black"},
        {'c':"#808000", 'name':"Olive"},
        {'c':"#8A2BE2", 'name':"Voilet"},
        {'c':"#A9A9A9", 'name':"DarkGray"},
        {'c':"#006400", 'name':"DarkGreen"},
        {'c':"#FF1493", 'name':"Pink"},
        {'c':"#FFD700", 'name':"Gold"},
        {'c':"#00FF00", 'name':"Lime"},
        {'c':"#FF0000", 'name':"Red"},
        {'c':"#F5F5F5", 'name':"White"},
        {'c':"#FFA500", 'name':"OrangeRed"},
        {'c':"#D2B48C", 'name':"Tan"},
        {'c':"#800080", 'name':"Purple"}
      ],
		 currentcolor:"", 
		    
};
	},
	computed: {
		   buttonLabel() {
      return (this.showPassword) ? "Hide" : "Show";
    }
	},
	methods:{
		chosecolor(n){
    this.currentcolor= n.target.value.c;

    console.log(this.currentcolor.c);
		},
		toggleShow() {
      this.showPassword = !this.showPassword;
    },
    signup(){

const data = { email:store.email,password:store.password ,color:store.color.c};
console.log(data);
  axios.post("http://localhost:4242/authentication", data)
    .then(response =>{console.log(response.data) 
    	store.email="";
    	store.password="";}
    	)
    .catch(error => {
      this.errorMessage = error.message;
      console.error("There was an error!", error);
    });
    }
	}
};
</script>
<style type="text/css" scoped>
.form {
	border: 1px solid gray;
	display: flex;
	flex-direction: column;
	width: 50%;
	justify-content: center;
	align-items: center;
	position: absolute;
	left: 25%;
	height: 35%;
}
input {
	height: 4vh;
	margin: 1vw;
}
.button-group {
	display: flex;
	justify-content: space-around;
	width: 100%;
}
.myButton {
	box-shadow: 0px 10px 14px -7px #276873;
	background: linear-gradient(to bottom, #599bb3 5%, #408c99 100%);
	background-color: #599bb3;
	border-radius: 21px;
	display: inline-block;
	cursor: pointer;
	color: #ffffff;
	font-family: Arial;
	font-size: 20px;
	font-weight: bold;
	padding: 13px 32px;
	text-decoration: none;
	text-shadow: 0px 1px 0px #3d768a;
}
.myButton:hover {
	background: linear-gradient(to bottom, #408c99 5%, #599bb3 100%);
	background-color: #408c99;
}
.myButton:active {
	position: relative;
	top: 1px;
}

.myButton1 {
	box-shadow: 3px 4px 0px 0px #8a2a21;
	background: linear-gradient(to bottom, #c62d1f 5%, #f24437 100%);
	background-color: #c62d1f;
	border-radius: 18px;
	border: 1px solid #d02718;
	display: inline-block;
	cursor: pointer;
	color: #ffffff;
	font-family: Arial;
	font-size: 17px;
	padding: 10px 20px;
	text-decoration: none;
	text-shadow: 0px 1px 0px #810e05;
}
.myButton1:hover {
	background: linear-gradient(to bottom, #f24437 5%, #c62d1f 100%);
	background-color: #f24437;
}
.myButton1:active {
	position: relative;
	top: 1px;
}

.input {
	padding: 3px;
	font-size: 20px;
	border-width: 4px;
	border-color: #cccccc;
	background-color: #ffffff;
	color: #000000;
	border-style: double;
	border-radius: 17px;
	box-shadow: 7px 2px 15px rgba(66, 66, 66, 0.75);
	text-shadow: 0px 0px 5px rgba(66, 66, 66, 0.75);
}
.input:focus {
	outline: none;
}
.eye{
	 width: 45px;height: 45px;
  transform: translateY(-10%);
	 
}

.colorshow{
	 height: 30px;
width: 20px;
border: 1px solid  black;}
</style>
