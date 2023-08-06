<template>
  <div>
    <el-row :gutter="50" style="margin-top: 40px; height: 715px;">
        <!-- 红球 -->
    <el-col :span="5" :push="2">
        <Ball :ballList="redBallList" ballStyle="color: #ff4242;" ballName="红球" @checkBall="checkBall"/>
    </el-col>

        <!--蓝球  -->
    <el-col :span="3" :push="2">
        <Ball :ballList="blueBallList" ballStyle=" color: #4545f1;" ballName="蓝球"  @checkBall="checkBall"/>
    </el-col>
    </el-row>
  </div>
</template>

<script>
import Ball from "./Ball.vue"

export default {
    components:{Ball},
    name :'Dlt',
        data(){
            const redBallList = [];
            for (let i = 1; i <= 35; i++) {
                redBallList.push({ballName:'red', ballnum: i, ischeck: false ,ballClass:{redBall:true,checkRedBall:false}});
            };

            const blueBallList = [];
            for (let i = 1; i <= 12; i++) {
                blueBallList.push({ballName:'blue', ballnum: i, ischeck: false ,ballClass:{buleBall:true,checkBuleBall:false}});
            }
          
           return {
              redBallList:redBallList,
              blueBallList:blueBallList,
              checkBallList:{redBallArr:[],blueArr:[]},
           }
        },
        methods: {
            //ball组件将选择的红球或篮球通过事件传过来
            checkBall(checkBallList,ballname){
                if(checkBallList.length != 0){
                    if(ballname === 'red'){
                        this.checkBallList.redBallArr = checkBallList;
                    }else if(ballname === 'blue'){
                        this.checkBallList.blueArr = checkBallList;  
                    }
                }else if(checkBallList.length == 0){
                    if(ballname === 'red'){
                        this.checkBallList.redBallArr = [];
                    }else if(ballname === 'blue'){
                        this.checkBallList.blueArr = [];  
                    }
                }
                console.log(this.checkBallList);
            }
        }
    }
</script>

<style lang="css" scoped >
   
</style>