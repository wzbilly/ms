
<template>
  <div id="app" class="index">
  <!--路由管道标签，任何符合某一路由(route)信息的组件都会在这个标签内展示出来 -->
  <router-link class="tab" v-bind:to="'/'">我的主页</router-link>
  <router-link class="tab" v-bind:to="'/mytable'">我的经历</router-link>
  <router-link class="tab" v-bind:to="'/random'">随机展示</router-link>
  <router-view class='index-body'></router-view>
  </div>
</template>

<style lang="css">
  @import "assets/style.css"
</style>
<script>

import 'bootstrap/dist/css/bootstrap.min.css'
 
import 'bootstrap/dist/js/bootstrap.min.js'

export default {
  name: 'app',

}
</script>
<!-- css格式 -->


