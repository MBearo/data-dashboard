<template>
  <div id="app">
    <div class="nav">

      <!-- logo -->
      <div class="logo">
        logo
      </div>
      <!-- 侧栏 -->
      <el-menu
        default-active="2"
        class="el-menu-vertical-demo"
        background-color="#041528"
        text-color="#fff"
        active-text-color="#ffd04b"
        :router="true"
      >
        <el-menu-item index="/">
        <i class="el-icon-data-analysis"></i>
          <span slot="title">总体大盘</span>
        </el-menu-item>
        <el-menu-item index="/Assets">
          <i class="el-icon-menu"></i>
          <span slot="title">数据实体</span>
        </el-menu-item>
        <el-menu-item index="Accuracy">
          <i class="el-icon-s-marketing"></i>
          <span slot="title">波动检测</span>
        </el-menu-item>
        <el-menu-item index="/Job" @click="getJob">
        <i class="el-icon-edit"></i>
          <span slot="title" >检测任务</span>
        </el-menu-item>
        <el-menu-item index="/Assessment">
        <i class="el-icon-finished"></i>
          <span slot="title">质量评估</span>
        </el-menu-item>
      </el-menu>
    </div>
    <div class="main">
      <!-- <el-menu
        :default-active="activeIndex"
        mode="horizontal"
        :router="true"
        @select="handleSelect"
        background-color="#041528"
        text-color="#fff"
        active-text-color="#"
      >
        <el-menu-item index="/"></el-menu-item>
        <el-menu-item index="/measure"></el-menu-item>
        <el-menu-item index="/job"></el-menu-item>
      </el-menu> -->
      <div class="header"></div>
      <router-view />
    </div>
  </div>
</template>
<script>
import axios from 'axios'
// import Job from '../views/job'

export default {
  data () {
    return {
      activeIndex: '/measure'
    }
  },
  methods: {
    getJob () {
      console.log(11111)
      axios
        .get('http://localhost:38080/api/v1/jobs')
        .then(res => {
          // console.log(res)
        })
    },
    handleClose (key, keyPath) {
      console.log(key, keyPath)
    }
  }
}
</script>
<style lang="scss">
html,
body {
  padding: 0;
  margin: 0;
  background-color: #f2f2f2;
  font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, 'Open Sans', 'Helvetica Neue', sans-serif;
}
#app {
  display: flex;
  height: 100vh;
}
.el-menu-vertical-demo {
  width: 200px;
  flex: 1 1 auto;
}
.nav{
  display: flex;
  flex-direction: column;
}
.main {
  flex: 1 1 auto;
  min-width: 0;
  // display: flex;
}
.header{
  height: 60px;
  background-color: #041528;
}
.logo{
  height: 60px;
  color: white;
  background-color:#ccc ;
}
</style>
