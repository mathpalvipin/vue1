<script setup>
import { RouterLink, RouterView } from 'vue-router'
import keyboard from '@/components/keyboard.vue'
import customform from '@/components/form.vue'
import login from '@/components/login.vue'
</script>

<template>

  <customform :password="password"  ></customform>
  <keyboard   @update="update"></keyboard>
  <!-- <h1>{{password}}</h1> -->
</template>


<script type="text/javascript">
  export default {
  data() {
    return 
    {password:"fdgf"}
  },
 methods:{
  update(n){
    console.log(n);
    this.password=n;
  }
 }
}
</script>
<style>


</style>
