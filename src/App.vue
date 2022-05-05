<template>
  <div class="container">
    <h1>姓名：{{ name }}</h1>
    <h2>年龄：{{ age }}</h2>
    <h3>性别：{{ sex }}</h3>
    <h4>分数: {{ sum() }}</h4>
    <h5>地址： {{ state.getAddress }}</h5>
    <button @click="say">点击</button>
    <button @click="editCount">更改数值</button>
  </div>
</template>

<script>
import { onBeforeMount, onBeforeUpdate, onMounted, onUpdated, reactive, ref, computed } from 'vue'
export default {
  name: "App",
  data() {
    return {
      sex: "男",
    };
  },
  setup(props, { emit }) {
    let name = "张三";
    let age = 20;
    let scoure = 0;
    let address = null;
    const state = reactive({
      count: 10,
      //计算属性
      getAddress: computed(()=>{
        address = 'xxx'
        return address
      })
    })
    console.log(state.count);
    //定义响应式变量
    const min = ref(0)
    console.log(min.value);
    function say() {
      alert("点击了");
    }
    function sum() {
      scoure = 100;
      return scoure;
    }
    // function getAddress() {
    //   address = "xxx";
    //   return address;
    // }
    function editCount() {
      min.value = 10
      console.log(min);
    }
    //组件加载完成
    onMounted(()=>{
      console.log('组件加载完成');
    })
    //组件加载前
    onBeforeMount(()=>{
      console.log('组件加载完成前');
    })
    //组件更新后
    onUpdated(()=>{
      console.log('数据更新后');
    })
    //组件更新前
    onBeforeUpdate(()=>{
      console.log('数据更新前');
    })
    return {
      name,
      age,
      address,
      scoure,
      state,
      say,
      sum,
      // getAddress,
      editCount
    };
  },
};
</script>