<template>
  <h1>我是APP</h1>
  <h3>姓名：{{ name }}</h3>
  <h3>姓名：{{ age }}</h3>
  <button @click="sayHello">说话</button>
</template>

<script>

export default {
  name: 'App',
  setup(){
    let name='张三'
    let age='18'
    
    function sayHello(){
      console.log(`我是${name},我${age}岁了，你好啊`);
    }
    return {
      name,
      age,
      sayHello
    }
  },
  
}
</script>

