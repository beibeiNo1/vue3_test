<template>
  <h1>我是APP</h1>
  <h3>和{{ sum }}</h3>
  <button @click="sum++">点我加1</button>
  <hr>
  <h3>当前信息为：{{ msg }}</h3>
  <button @click="msg+='!'">修改信息</button>
  <hr>
  <h3>姓名：{{ person.name }}</h3>
  <h3>年龄：{{ person.age }}</h3>
  <button @click="person.name+='~'">修改姓名</button>
  <button @click="person.age++">增长年龄</button>
  <hr>
  <h3>{{ person.job.j1.salary }}K</h3>
  <button @click="person.job.j1.salary++">涨薪</button>
</template>

<script>
import { ref,reactive,watch } from 'vue'


export default {
  name: 'App',
  setup(){
    let sum = ref(0)
    let msg = ref('你好啊')
    let person = reactive({
      name: '张三',
      age: 18,
      job: {
        j1: {
          salary: 20,
        },
      },
    })
    // person.salary=20
    // 1 单个
    // watch(sum,(newV,oldV)=>{
    //   console.log('sum被修改了',newV,oldV);
    // })
    // 2 多个，传数组
    // watch([sum,msg],(newV,oldV)=>{
    //   console.log('sum被修改了',newV,oldV);
    // })
    // 3 监听对象，得不到oldV
    // watch(person,(newV,oldV)=>{
    //   console.log('sum被修改了',newV,oldV);
    // })
    // 4 第一个参数传对象的属性，可以得到oldV
    // watch(()=>person.name,(newV,oldV)=>{
    //   console.log('sum被修改了',newV,oldV);
    // })
    // 5 第一个参数传对象的属性，可以得到oldV（可传数组）
    // watch([()=>person.name,()=>person.age],(newV,oldV)=>{
    //   console.log('sum被修改了',newV,oldV);
    // })
    // 6 第一个参数传对象的属性，可以得到oldV（可传数组）
    watch(()=>person.job,(newV,oldV)=>{
      console.log('sum被修改了',newV,oldV);
    },{deep:true},)

    return {
      sum,
      msg,
      person
    }
  },
  
}
</script>

