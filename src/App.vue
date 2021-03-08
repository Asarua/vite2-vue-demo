<template>
  <button @click="consoleWithHw">click hw</button>
  <img alt="Vue logo" src="./assets/logo.png" />
  <HelloWorld
    @changeLog="changeLog"
    @changeName="changeName"
    ref="hw"
    msg="Hello Vue 3 + Vite"
  />
</template>

<script setup>
// 直接使用组件
import HelloWorld from '@/components/HelloWorld.vue'
import { ref } from 'vue'

// 使用ref，只能使用expose导出的东西
const hw = ref(null)
const consoleWithHw = () => {
  hw.value.changeCount()
  console.log(hw.value)
}

const changeLog = () => {
  console.log('this is changeLog')
}

const changeName = () => {
  console.log('this is changeName')
}

// This starter template is using Vue 3 experimental <script setup> SFCs
// Check out https://github.com/vuejs/rfcs/blob/script-setup-2/active-rfcs/0000-script-setup.md
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