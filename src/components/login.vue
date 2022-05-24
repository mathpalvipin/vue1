<template>


<div class="form">
	 
	 	
	 	<input type="email" class="input" />
	 	<input type="" class="input" v-model="password">
	 
	 	<div class=" button-group">
	 		
	 		<router-link class="myButton1" to="/signup">not register yet !</router-link> 
	
	 	<a href="#" class="myButton">login</a>
	 	
	 </div>
	 
</div>

</template>

<script type="text/javascript">
	export default {
props:{
	password:String 
}

}
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
	.button-group{
		display: flex;
		justify-content: space-around;
		width: 100%;
	}
	.myButton {
	box-shadow: 0px 10px 14px -7px #276873;
	background:linear-gradient(to bottom, #599bb3 5%, #408c99 100%);
	background-color:#599bb3;
	border-radius:21px;
	display:inline-block;
	cursor:pointer;
	color:#ffffff;
	font-family:Arial;
	font-size:20px;
	font-weight:bold;
	padding:13px 32px;
	text-decoration:none;
	text-shadow:0px 1px 0px #3d768a;
}
.myButton:hover {
	background:linear-gradient(to bottom, #408c99 5%, #599bb3 100%);
	background-color:#408c99;
}
.myButton:active {
	position:relative;
	top:1px;
}



.myButton1 {
	box-shadow: 3px 4px 0px 0px #8a2a21;
	background:linear-gradient(to bottom, #c62d1f 5%, #f24437 100%);
	background-color:#c62d1f;
	border-radius:18px;
	border:1px solid #d02718;
	display:inline-block;
	cursor:pointer;
	color:#ffffff;
	font-family:Arial;
	font-size:17px;
	padding:10px 20px;
	text-decoration:none;
	text-shadow:0px 1px 0px #810e05;
}
.myButton1:hover {
	background:linear-gradient(to bottom, #f24437 5%, #c62d1f 100%);
	background-color:#f24437;
}
.myButton1:active {
	position:relative;
	top:1px;
}



.input {
     padding: 3px;
     font-size: 20px;
     border-width: 4px;
     border-color: #CCCCCC;
     background-color: #FFFFFF;
     color: #000000;
     border-style: double;
     border-radius: 17px;
     box-shadow: 7px 2px 15px rgba(66,66,66,.75);
     text-shadow: 0px 0px 5px rgba(66,66,66,.75);
}
.input:focus {
     outline:none;
}
     

</style>