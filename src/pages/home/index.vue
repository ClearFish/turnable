<script setup>
import TrunAble from "@/components/turnable.vue"
import { onMounted, ref } from "vue"
let leftVal = ref(null)
let titleList = ref([
  {name:'Relatório',value:'1'},
  {name:'Minha Referencia',value:'2'}
])
let scrollList = ref([
  {account:'1',name:'Kobe Bryant',bonous:100},
  {account:'2',name:'Kobe Bryant',bonous:100},
  {account:'3',name:'Kobe Bryant',bonous:100},
  {account:'4',name:'Kobe Bryant',bonous:100},
  {account:'5',name:'Kobe Bryant',bonous:100},
  {account:'6',name:'Kobe Bryant',bonous:100},
  {account:'7',name:'Kobe Bryant',bonous:100},
  {account:'8',name:'Kobe Bryant',bonous:100},
  {account:'9',name:'Kobe Bryant',bonous:100},
  {account:'10',name:'Kobe Bryant',bonous:100},
  {account:'11',name:'Kobe Bryant',bonous:100},
  {account:'12',name:'Kobe Bryant',bonous:100},
  {account:'13',name:'Kobe Bryant',bonous:100},
  {account:'14',name:'Kobe Bryant',bonous:100},
  {account:'15',name:'Kobe Bryant',bonous:100},
  {account:'16',name:'Kobe Bryant',bonous:100},
  {account:'17',name:'Kobe Bryant',bonous:100},
  {account:'18',name:'Kobe Bryant',bonous:100},
  {account:'19',name:'Kobe Bryant',bonous:100},
  {account:'20',name:'Kobe Bryant',bonous:100}
])
onMounted(()=>{
  leftVal.value = "calc(10% - 10px)"
})
</script>

<template>
  <div class="home_box">
    <div class="top_container">
      <div class="top_box">
        <img src="@/assets/game/spin-1.png" alt="" class="left_img">
        <p class="moner"> R$ 95.79</p>
        <div class="scar">
          <img src="@/assets/game/pix.png" alt="">
          <p class="right">SACAR</p>
        </div>
      </div>
      <div class="center_box">
        <p class="title">95.79%</p>
        <div class="progress">
          <div class="point" :style="{left:leftVal}"></div>
        </div>
      </div>
      <div class="needCash">
        Ainda é necessário 
        <span data-v-449fc671="" class="needCashNum">4.21</span>  
        para realizar do saque 
      </div>
    </div>
    <TrunAble/>
    <div class="expre_time">
      <p class="title">Expira time</p>
      <p class="value">02:00</p>
    </div>
    <div class="share_box">
      <p class="value"> Convide amigos para ajudar com saques </p>
      <img src="@/assets/game/share_fill.svg" alt="">
    </div>
    <div class="list_box">
      <div class="top_title">
          <p v-for="(item,index) in titleList" :key="index">{{item.name}}</p>
      </div>
      <div class="scroll_content">
        <div class="scroll_box">
          <div class="scroll_cont">
            <div class="item" v-for="(item,index) in scrollList" :key="index">
              <p>{{item.account}}</p>
              <p>{{item.name}}</p>
              <p>{{item.bonous}}</p>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped lang="scss">
.home_box {
  width: 100%;
  height: 100%;
  padding: 50px 0;
  .top_container {
    background-color: rgb(35, 35, 39);
    padding: 20px;
    border-radius: 8px;
    .top_box {
      display: flex;
      align-items: center;
      justify-content: space-between;
      .left_img {
        width: 52px;
        height: 37px;
      }
      .moner {
        color: #6ddf38;
        font-size: 20px;
        font-weight: 800;
      }
      .scar {
        padding: 4px 12px;
        border-radius: 8px;
        display: flex;
        justify-content: center;
        align-items: center;
        gap: 4px;
        font-size: 14px;
        font-weight: 700;
        color: #fff;
        background: #6ddf38;
        img {
          width: 15px;
          height: 15px;
        }
      }
    }
    .center_box {
      margin-top: 8px;
      .title{
        color: #fff;
        text-align: right;
      }
      .progress {
        width: 100%;
        height: 10px;
        border-radius: 5px;
        background: #6ddf38;
        position: relative;
        .point {
          width: 10px;
          height: 10px;
          border-radius: 5px;
          background: #fff;
          position: absolute;
          top: 0px;
        }
      }
    }
    .needCash {
      margin-top: 10px;
      color: #fff;
      text-align: center;
      .needCashNum {
        color: #6ddf38;
        font-weight: 600;
      }
    }
  }
  .expre_time {
    margin-top: 20px;
    display: flex;
    justify-content: center;
    align-items: center;
    color: rgb(135, 149, 177);
    .value {
      color: #fff;
      margin-left: 4px;
    }
  }
  .share_box {
    padding: 4px 10px;
    width: 100%;
    background: #202124;
    border-radius: 4px;
    margin-top: 10px;
    color: #fff;
    font-size: 14px;
    display: flex;
    justify-content: space-between;
    align-items: center;
    box-sizing: border-box;
    img {
      width: 16px;
      height: 16px;
    }
  }
  .list_box {
    margin-top: 10px;
    .top_title {
      display: flex;
      width: 100%;
      height: 40px;
      align-items: center;
      background: #202124;
      p {
        flex: 1;
        color: #9c9c9c;
        text-align: center;
        font-size: 16px;
      }
    }
    .scroll_content {
      width: 100%;
      .scroll_box {
        height: 200px;
        overflow: hidden;
        .scroll_cont {
          height: 100%;
          // transition-timing-function: linear;
          // transition-duration: 12s;
          // transform: translateY(-600px);
          animation-name: scrollY;
          animation-duration: 8s;
          animation-iteration-count: infinite;
          animation-fill-mode:forwards;
          animation-timing-function: linear ;
          .item {
            display: flex;
            justify-content: space-between;
            height: 40px;
            align-items: center;
            padding: 0 10px;
            box-sizing: border-box;
            color: #fff;
          }
        }
      }
    }
  }
}
@keyframes scrollY {
  from {
    transform: translateY(0px);
  }
  to {
    transform: translateY(-600px);
  }
}
</style>
