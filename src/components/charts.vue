<template>
  <div>
    <div class="my-msg">
      <div class="my-msg-title">个人信息</div>
      <div class="my-msg-detial">
        <span v-for='item in msg'>{{item}}</span>
      </div>
      
    </div>
    <div class="my-msg">
      <div class="my-msg-title">求职意向</div>
      <div class="my-msg-detial">
        <span v-for='item in purp'>{{item}}</span>
      </div>
      
    </div>
    <div class="my-msg">
      <div class="my-msg-title">兴趣爱好</div>
      <div class="my-msg-detial">
        <span v-for='item in hobby'>{{item}}</span>
      </div>
      
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
  name: 'HelloWorld',
  data () {
    return {
      msg: ['王智彬','男','26岁','4年前端经验','18642812477','ww739139799@163.com'],
      purp:['web前端工程师','13k-18k','五险一金'],
      hobby:['郊游','游泳','电子游戏','漫画','小说'],
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
    this.drawLine();
  },
  methods: {
    drawLine(){
        var that = this;
         // 基于准备好的dom，初始化echarts实例
        let myChart = this.$echarts.init(document.getElementById('chart'))

      


       
        // 获取技能名称与数值的数组
        let skillname = [];
        let skillnum = [];
        for(let i = 0;i<this.skills.length;i++){
          skillname.push(this.skills[i].name);
          skillnum.push(this.skills[i].num);
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
       
 
    },

  }


}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1, h2 {
  font-weight: normal;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
