<template>
  <h1>{{ msg }}</h1>

  <button @click="state.count++">count is: {{ state.count }}</button>
  <p>
    Edit
    <code>components/HelloWorld.vue</code> to test hot module replacement.
  </p>

  <button @click="changeLog">click for changeLog</button>
  <button @click="changeName">click for changeName</button>
</template>

<script setup>
import { defineProps, reactive, useContext, defineEmit } from 'vue'

// 获取全局上下文，即setup中第二个参数
const ctx = useContext()
console.log(ctx)

// 获取props
const props = defineProps({
  msg: String
})

// 声明emit
const emits = defineEmit(['changeName', 'changeLog'])
// 使用emit的第一种方式
const changeLog = () => {
  emits('changeLog')
}

// 使用emit的第二种方式
const changeName = () => {
  ctx.emit('changeName')
}

// 当前组件导出的东西，外部组件使用ref引用的时候，只能获取到expose导出的东西
ctx.expose({
  changeCount() {
    state.count += 2
    console.log(props)
  }
})

// 声明变量
const state = reactive({ count: 0 })
</script>

<style scoped>
a {
  color: #42b983;
}
</style>