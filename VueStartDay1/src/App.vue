<!-- <script setup>
// This starter template is using Vue 3 <script setup> SFCs
// Check out https://vuejs.org/api/sfc-script-setup.html#script-setup
import HelloWorld from './components/HelloWorld.vue'
</script> -->
<script>
  // 声明式渲染
  export default{
    data() {
      return {
        num:0,
        uname:"张三",
        h2msg:"<h2>收拾收拾</h2>",
        id:"id1",
        objectOfAttrs: {
          id: 'container',
          class: 'wrapper'
        },
        attribute:'id',
        attribute_on:'dblclick'
      }
    },
    methods: {//写入模板的JS方法集合
      changevalue: function(){
        // this 指向 vue实例
        this.num =3;
        this.uname = "李四";
      },
      changecolor:function () {
        this.id = "id2";
        }
    },
  }
  var self = this;
</script>
<template>
<!-- 组件实例的所有 property，无论如何定义，都可以在组件的模板中访问。 -->
  <div>
    <a href="https://vitejs.dev" target="_blank">
      <img src="/vite.svg" class="logo" alt="Vite logo" />
    </a>
    <a href="https://vuejs.org/" target="_blank">
      <img src="./assets/vue.svg" class="logo vue" alt="Vue logo" />
    </a>
    <HelloWorld msg="Vite + Vue" />
    <!-- 双大括号语法为插值  通过使用 v-once 指令，你也能执行一次性地插值，当数据改变时，插值处的内容不会更新。但请留心这会影响到该节点上的其它数据绑定 它使用的是“Mustache”语法 (即双大括号) -->
    <span>{{num}}</span>
    <span v-once>{{uname}}</span>
    <p>{{h2msg}}</p>
    <!-- v-html显示 html标签 -->
    <p v-html="h2msg"></p>
    <button @click="changevalue">更改实体的值</button>
    <!-- v-bind 动态绑定属性内容 -->
    <!-- <p id="id1">这样是个P标签</p> -->
    <p v-bind:id="id">这是一个P标签</p>
    <!-- v-bind可以简写成: -->
    <p :id="id">这是一个P标签 v-bind简写</p>
    <!-- 布尔型 attribute 依据 true / false 值来决定 attribute 是否应该存在于该元素上。disabled(禁用) 就是最常见的例子之一。 -->
    <p >
      <button :disabled="true" >Button_true</button>
      <button :disabled="false">Button_false</button>
    </p>
    <!-- 如果你有像这样的一个包含多个 attribute 的 JavaScript 对象 通过不带参数的 v-bind，你可以将它们绑定到单个元素上 -->
    <p :="objectOfAttrs"></p> 
    <button @click="changecolor">更改实体的ID</button>
    <!-- 使用JavaScript表达式 仅支持表达式，也就是一段能够被求值的 JavaScript 代码-->
    <button @click="id='id2'">更改实体的ID</button>
    <span>{{num+1}}</span>
    <span >{{uname.split('').reverse().join('')}}</span>
    <!-- v-on 监听DOM事件 简写 @ -->
    <button v-on:click="id='id2'">更改实体的ID</button>
  </div>

  <div>
    <!-- 动态参数 -->
    <!-- 同样在指令参数上也可以使用一个 JavaScript 表达式，需要包含在一对方括号内[] -->
    <!-- 动态参数表达式因为某些字符的缘故有一些语法限制，比如空格和引号，在 HTML attribute 名称中都是不合法的 -->
    <p :[attribute]="id">这是一个P标签 动态参数</p>
    <button @[attribute_on]="attribute='class'">点击修改动态属性——P</button>
    <button @click="attribute_on='focus'">点击修改动态属性——but</button>
  </div>
</template>

<style scoped>
.logo {
  height: 6em;
  padding: 1.5em;
  will-change: filter;
}
.logo:hover {
  filter: drop-shadow(0 0 2em #646cffaa);
}
.logo.vue:hover {
  filter: drop-shadow(0 0 2em #42b883aa);
}
#id1{
  color: aqua;
}
#id2{
  color: red;
}
</style>
