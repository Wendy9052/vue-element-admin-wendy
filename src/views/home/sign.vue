<template>
  <div>
      <div class="about-container">
      <top-bar :title="title"></top-bar>
      <div class="step_box">
        <!-- 线 -->
        <div class="line"></div>
        <!-- 3个圆点 -->
        <div class="dot_box">
          <div class="dot">
            <img :src="tick_icon" alt="">
          </div>
          <div class="dot">
            <img :src="tick_icon" alt="">
          </div>
          <div class="dot dot_active"></div>
        </div>

        <!-- 3个文字信息 -->
        <div class="text_box">
          <div class="text">基础信息</div>
          <div class="text">身份证件</div>
          <div class="text">签署协议</div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import topBar from '@/components/topBar'
import tick_icon from "@/assets/img/tick_s.png"

export default {
    name:"sign",
    components:{
        topBar
    },
    data(){
        return{
            title: '生命绿洲众包信息注册',
            tick_icon:tick_icon
        }
    }
}
</script>

<style lang="scss">
.step_box {
    height: 68px;
    background: #1cb49d 1%;
    padding-top: 10px;
    .text_box {
      display: flex;
      justify-content: space-between;
      padding: 6px 18px;
      .text {
        font-size: 14px;
        color: #fff;
      }
    }
    .line {
      width: 75%;
      height: 4px;
      background: #fff;
      margin: 15px auto 0;
    }
    .dot_box {
      margin: 0 auto;
      // background: pink;
      width: 78%;
      display: flex;
      display: flex;
      justify-content: space-between;
      .dot {
        width: 16px;
        height: 16px;
        background: #fff;
        border-radius: 50%;
        margin-top: -10px;
        color: #1CB49D;
        font-weight: bold;
        overflow: hidden;
        display: flex;
        justify-content: center;
        align-items: center;
        img{
          width: 100%;
          height: 100%;
          margin: 5px;
        }
      }
      .dot_active {
        width: 12px;
        height: 12px;
        background: #ffb253;
        border: 8px solid #fff;
        border-radius: 50%;
        margin-top: -16px;
      }
    }
  }
</style>