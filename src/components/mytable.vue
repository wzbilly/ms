<template>
  <div id="mytable">
    <div class="my-msg">
        <div class="my-msg-title">工作经历</div>
        <table class='my-table'>
            <tr>
              <th style="width:20%">单位名称</th>
              <th style="width:20%">在职时间</th>
              <th>主要职责</th>
            </tr>
            <tr v-for="item in workdata">
              <td>{{item.name}}</td>
              <td>{{item.time}}</td>
              <td>
                <span v-for="list in item.detials">{{list}}</span>
              </td>
            </tr>
        </table>
    </div>
    <div class="my-msg">
      <div class="my-msg-title">项目经验</div>
           <table class='my-table table'>
            <tr>
              <th style="width:20%">项目名称</th>
              <th style="width:20%">项目时间</th>
              <th>项目简介</th>
            </tr>
            <tr v-for="item in tabledata">
              <td>{{item.name}}</td>
              <td>{{item.date}}</td>
              <td>
                <span v-for="list in item.detials">{{list}}</span>
              </td>
            </tr>
          </table>
    </div>
  </div>
</template>

<script>
export default {
  name: 'mytable',
  data(){
    return{
      tabledata:[
        { 
          name:'哆唻客点餐平台(小程序)',
          date:'2018.9-2019.4',
          detials:[
            '1.与产品经理、项目经理沟通，了解客户需求与项目目标。',
            '2.与UI设计师沟通，引导设计师完成更好用户体验的页面。',
            '3.与后台工程师沟通，完成数据渲染与交互，合理分配开发时间。',
            '4.完成前端主体框架，编写主要页面与组件。',
            '5.与测试工程师沟通，完善页面展示效果，优化页面。'
          ]
        },
        {
          name:'跨境美屋商城(公众号，小程序,pc端)',
          date:'2017.1-至今',
          detials:[
           '1.使用html，css完成页面响应式布局，适配大部分主流手机。',
           '2.根据客户要求与UI实现pc端和移动端页面展示效果。',
           '3.根据项目要求使用原生js或jq完成页面动画。',
           '4.使用canvas或DOM操作完成简单的页面交互效果，制作移动端小游戏。'
          ]
        },
        {
          name:'手机端校园点餐平台',
          date:'2018.12-2019.3',
          detials:[
           '1.使用node.js搭建项目。',
           '2.模仿vue-cli开源案例并根据具体需求完成项目前端页面。',
           '3.与后台工程师沟通，完成前端数据渲染与交互操作。'
          ]
        },
        {
          name:'功能性网站开发',
          date:'2017.1-至今',
          detials:[
           '1.使用html，css完成页面响应式布局，使页面适配所有主流浏览器。',
           '2.根据客户要求与UI实现pc端和移动端页面展示效果。',
           '3.使用ajax技术完成数据渲染。',
           '4.与后台工程师沟通，通过svn进行产品迭代。',
          ' 5.灵活应用各类插件与接口，实现客户要求的功能。'
          ]
        },
        {
          name:'企业展示类网站，企业官网开发',
          date:'2015.3-2016.10',
          detials:[
            '1.使用html，css完成页面响应式布局，使页面适配所有主流浏览器。',
            '2.根据客户要求与UI实现pc端和移动端页面展示效果。',
            '3.根据项目要求使用原生js或jq完成页面动画。',
            ' 4.使用ajax技术完成数据渲染。',
            '5.灵活应用各类插件与接口，实现客户要求的功能。'
          ]
        },
      ],
      workdata:[
        {
          name:'大连晟丰原科技',
          time:'2016.10-至今',
          detials:[
            '1.负责公众号项目，商城项目开发与维护。',
            '2.开发公众号活动小游戏，实现客户满意的页面游戏动画。',
            '3.通过与后台工程师沟通完成数据渲染。',
            '4.开发微信小程序，负责前端任务分配与时间安排。',
            '5.使用Node.js搭建小型项目的前端页面。'
          ]
        },
        {
          name:'大连科辰软件有限公司',
          time:'2015.3-2016.10',
          detials:[
            '1.负责前端页面的开发与重构。',
            '2.与UI设计师沟通，完成符合客户要求的前端效果展示。',
            '3.与后台工程师沟通，进行简单的数据渲染。'
          ]
        },
      ]
    }
  },
  mounted(){
    
  },
  methods:{
   
  }
}
</script>
<style>
#about {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
