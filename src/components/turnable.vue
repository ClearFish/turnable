<script setup>
import Spin1 from "@/assets/game/spin-1.png"
import Spin2 from "@/assets/game/spin-2.png"
import Spin3 from "@/assets/game/spin-3.png"
import Spin4 from "@/assets/game/spin-4.png"
import Spin5 from "@/assets/game/spin-5.png"
import LuckyWheel from '@/utils/luck.ts';
import { onMounted, ref } from 'vue'
const PRIZELIST = ref([
  { desc: '中奖一元', bgColor: '#195C26', color: '#FFF', imageId: Spin1 },
  { desc: '谢谢惠顾', bgColor: '#EB9713', color: '#FEDF1A', imageId: '',number:1 },
  { desc: '中奖二元', bgColor: '#195C26', color: '#FFF', imageId: Spin2 },
  { desc: '谢谢惠顾', bgColor: '#EB9713', color: '#FEDF1A', imageId: '',number:1000 },
  { desc: '中奖三元', bgColor: '#195C26', color: '#FFF', imageId: Spin4 },
  { desc: '谢谢惠顾', bgColor: '#EB9713', color: '#C02A16', imageId: '',number:50 },
  { desc: '中奖四元', bgColor: '#195C26', color: '#FFF', imageId:  Spin1},
  { desc: '谢谢惠顾', bgColor: '#EB9713', color: '#FFF', imageId: Spin5 },
]);
let luckyWheelRef = ref(null)
onMounted(()=>{
  luckyWheelRef.value = new LuckyWheel({
      selector: '.pie',
      segsLen: PRIZELIST.length,
      onFinished: (index) => {
        console.log('finished-->', index);
      },
  })
})
  const handleStart = () => {
    luckyWheelRef.value.play();
    setTimeout(()=>{
      handleEnd()
    },5000)
  };

  const handleEnd = () => {
    luckyWheelRef.value.stop(7);
  };
</script>

<template>
<div class="big_box">
    <div class="pie">
        <div class="slice" 
            v-for="(item,index) in PRIZELIST" 
            :key="index"
            :style="{ backgroundColor: item.bgColor,
                    color: item.color,
                    transform: `rotate(${index * 45}deg) skewY(-45deg)`}"
        >
            <div class="content">
            <img v-if="item.imageId" :src="item.imageId" alt="">
            <p class="title" v-if="item.number" :style="{color:item.color}">{{item.number}}</p>
            </div>
        </div>
    </div>
    <div class="center_bg" @click="handleStart"></div>
    <div class="bg_box"></div>
    <div class="pointer_box"></div>
</div>

  
</template>

<style scoped lang="scss">
.big_box {
  width: 320px;
  height: 400px;
  text-align: center;
  margin: 30px auto;
  position: relative;
  display: flex;
  align-items: center;
  justify-content: center;
  padding-top: 60px;
  box-sizing: border-box;
    // 扇形布局核心样式
  .pie {
    width: 244px;
    height: 244px;
    position: relative;
    border-radius: 50%;
    overflow: hidden;
    transform: rotate(0deg);
    z-index: 2;
    .slice {
      overflow: hidden;
      position: absolute;
      top: 0;
      right: 0;
      width: 50%;
      height: 50%;
      // css 画扇形 https://www.jianshu.com/p/3ab7e71ff810
      transform-origin: 0% 100%;
      text-align: left;
      display: flex;
      .content {
        // transform-origin: 0% 100%;
        // skew 效果反转 https://www.v2ex.com/t/394630
        // transform: skewY(45deg) rotate(-45deg);
        transform: skewY(45deg) rotate(25deg);
        width: 100%;
        position: absolute;
        left: -20px;
        bottom: 25px;
        text-align: center;
        padding-right: 15px;
        box-sizing: border-box;
        font-weight: bolder;
        font-size: 14px;
        img {
          width: 30px;
          height: auto;
        }
      }
    }
  }
  .center_bg {
      position: absolute;
      top: 57%;
      left: 50%;
      transform: translate(-50%,-50%);
      background: url("@/assets/game/draw.png") no-repeat center;
      background-size: 100% 100%;
      width: 100px;
      height: 90px;
      z-index: 3;
    }
  .bg_box {
    width: 100%;
    height: 100%;
    background: url("@/assets/game/big_bg.png") no-repeat center;
    background-size: 100% 100%;
    position: absolute;
    top: 0;
    left: 0;
    z-index: 1;
  }
  .bg_box {
    
  }
  .pointer_box {
    position: absolute;
    left: 50%;
    background: url("@/assets/game/pointer.png") no-repeat center;
    background-size: 100% 100%;
    transform: translateX(-50%);
    width: 100px;
    height: 62px;
    z-index: 3;
    top: 78px;
  }
}
</style>
