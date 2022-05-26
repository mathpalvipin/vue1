<script setup>
import { RouterLink, RouterView } from 'vue-router'
import keyboard from '@/components/keyboard.vue'


</script>

<template>

 <router-view ></router-view>
  <keyboard  ></keyboard>
  <!-- <h1>{{password}}</h1> -->
</template>


<script type="text/javascript">
  import {store} from './store.js'
</script>
<style>


</style>
