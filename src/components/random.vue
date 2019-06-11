<template>
  <div id="random">
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
    <div id="chart" :style="{width: '800px', height: '500px'}">
   
    </div>
  </div>
</template>

<script>
// 引入基本模板
let echarts = require('echarts/lib/echarts')
// 引入柱状图组件
require('echarts/lib/chart/bar')
// 引入提示框和title组件
require('echarts/lib/component/tooltip')
require('echarts/lib/component/title')
export default {
  name: 'random',
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
      skills:[
        {
          name:'html',
          num:90
        },
        {
          name:'css',
          num:90
        },
        {
          name:'javascript',
          num:80
        },
        {
          name:'jQuery',
          num:80
        },
        {
          name:'Vue.js',
          num:75
        },
        {
          name:'Node.js',
          num:60
        },
        {
          name:'ES6',
          num:75
        },
      ]
    }
  },
  mounted(){
    this.changetable();
    this.drawLine();
  },
  methods:{
    changetable() {
        var getRandomArrayElements = (arr,count) => {
           var shuffled = arr.slice(0), i = arr.length, min = i - count, temp, index;
            while (i-- > min) {
                index = Math.floor((i + 1) * Math.random());
                temp = shuffled[index];
                shuffled[index] = shuffled[i];
                shuffled[i] = temp;
            }
            return shuffled.slice(min);
        }
        this.tabledata = getRandomArrayElements(this.tabledata,3);
        let time = 10;  
        var that  = this;  
        setInterval(function () {
          time--;
          if(time <= 0){
            that.tabledata = getRandomArrayElements(that.tabledata,3);
            
            time = 10;
          }
        },1000)
    },
    drawLine(){
        var that = this;
         // 基于准备好的dom，初始化echarts实例
        let myChart = this.$echarts.init(document.getElementById('chart'))

        

        // 获取技能名称与数值的数组
        let skillname = [];
        let skillnum = [];
        for(let i = 0;i<this.skills.length;i++){
          skillname.push(this.skills[i].name);
          skillnum.push( Math.floor(Math.random()*(100 - 1) + 1));
        }
        
        // 绘制图表
        myChart.setOption({
                title: { 
                  text: '我的能力值' ,
                  textStyle:{
                    color:'#157c8c',
                    fontSize: 20,
                    fontWeight: 'bold',
                  }
                },
                tooltip: {},
                color:['#157c8c'],
                xAxis: {
                    data: skillname
                },
                yAxis: {},
                series: [{
                    name: '能力值',
                    type: 'bar',
                    data: skillnum
                }]
        });
        let time = 10;    
        setInterval(function () {
          time--;
          if(time <= 0){
           
            skillname = [];
            skillnum = [];
            // 获取技能名称与数值的数组
            for(let i = 0;i<that.skills.length;i++){
              skillname.push(that.skills[i].name);
              skillnum.push(Math.floor(Math.random()*(100 - 1) + 1));
            }
 
            // 绘制图表
            myChart.setOption({
                title: { 
                  text: '我的能力值' ,
                  textStyle:{
                    color:'#157c8c',
                    fontSize: 20,
                    fontWeight: 'bold',
                  }
                },
                tooltip: {},
                color:['#157c8c'],
                xAxis: {
                    data: skillname
                },
                yAxis: {},
                series: [{
                    name: '能力值',
                    type: 'bar',
                    data: skillnum
                }]
            });
            time = 10;
          }
         
          
        },1000)
 
    },
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
