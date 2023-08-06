<template>
    <div>
        <h3 :style="ballStyle">{{ballName}}</h3>
        <span v-for="ball in ballList" :key="ball.ballnum" :class="ball.ballClass" @click="checkBall(ball)">
            {{ ball.ballnum }}
        </span>

    </div>
   
</template>

<script>
export default {
    name: 'ball',
    props:['ballList','ballStyle','ballName'],
    data() {
        return{
            checkBallList:[],
        }
    },
    methods:{
        checkBall(ball){
            //console.log(ball)
            ball.ischeck = !ball.ischeck
            //样式取反
            for (const key in ball.ballClass) {
                if (Object.hasOwnProperty.call(ball.ballClass, key)) {
                    ball.ballClass[key] = !ball.ballClass[key];
                }
            }
            
            if(ball.ischeck){
                //选中球添加进数组
                if(ball.ballName ==='red'){
                    this.checkBallList.push(ball);

                }else if (ball.ballName === 'blue'){
                    this.checkBallList.push(ball);
                }
            }else{
                //取消球选择从数组中移除
                if(ball.ballName ==='red'){
                    this.checkBallList = this.checkBallList.filter( ball => ball.ischeck === true )
                }else if(ball.ballName === 'blue'){
                    this.checkBallList = this.checkBallList.filter( ball => ball.ischeck === true )
                }
                
            }
            //把红球或蓝球的选中list给dlt组件
            this.$emit('checkBall',this.checkBallList, ball.ballName)
        },
    }
}
</script>

<style  lang="css" scoped >
    .redBall {
        display: inline-block;
        width: 30px;
        height: 30px;
        border-radius: 50%;
        /* background-color: #ff4242; */
        background-color: white;
        /* color: white; */
        color: #ff4242;
        text-align: center;
        line-height: 30px;
        font-weight: bold;
    }

    .buleBall {
        display: inline-block;
        width: 30px;
        height: 30px;
        border-radius: 50%;
        /* background-color: #4545f1; */
        background-color: white;
        /* color: white; */
        color: #4545f1;
        text-align: center;
        line-height: 30px;
        font-weight: bold;
    }

    .checkRedBall{
        display: inline-block;
        width: 30px;
        height: 30px;
        border-radius: 50%;
        background-color: #ff4242;
        color: white;
        text-align: center;
        line-height: 30px;
        font-weight: bold;
    }

    .checkBuleBall{
        display: inline-block;
        width: 30px;
        height: 30px;
        border-radius: 50%;
        background-color: #4545f1;
        color: white;
        text-align: center;
        line-height: 30px;
        font-weight: bold;
    }
</style>
