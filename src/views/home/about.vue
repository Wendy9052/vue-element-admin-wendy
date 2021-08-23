<!-- 身份证件 -->
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
          <div class="dot dot_active"></div>
          <div class="dot"></div>
        </div>

        <!-- 3个文字信息 -->
        <div class="text_box">
          <div class="text">基础信息</div>
          <div class="text">身份证件</div>
          <div class="text">签署协议</div>
        </div>
      </div>
    </div>

    <!-- 上传证件照片 -->
    <div class="upload_box">
      <div class="upload_text">上传身份证照片</div>
      <!-- 人面像 -->
      <div class="id_card">
        <img :src="id_head" alt="">
        <div class="camera_box">
          <img :src="camera" alt="">
          <div class="tips_msg">点击拍摄身份证人像面</div>
        </div>
      </div>  
      <!-- 国徽 -->
      <div class="id_card">
        <img :src="id_badge" alt="">
        <div class="camera_box">
          <img :src="camera" alt="">
          <div class="tips_msg">点击拍摄身份证国徽面</div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
// 请求接口
import { getUserInfo } from '@/api/user.js'
import { mapGetters } from 'vuex'
import topBar from '@/components/topBar'

import id_head from "@/assets/img/id_head.png"
import id_badge from "@/assets/img/id_badge.png"
import camera from "@/assets/img/camera.png"
import tick_icon from "@/assets/img/tick_s.png"


export default {
  data() {
    return {
      title: '生命绿洲众包信息注册',
      id_head:id_head,
      id_badge:id_badge,
      camera:camera,
      tick_icon:tick_icon
    }
  },
  components: {
    topBar
  },
  computed: {
    ...mapGetters(['userName'])
  },
  mounted() {
    this.initData()
  },
  methods: {
    // 请求数据案例
    initData() {
      // 请求接口数据，仅作为展示，需要配置src->config下环境文件
      const params = { user: 'sunnie' }
      getUserInfo(params)
        .then(() => {})
        .catch(() => {})
    },
    // Action 通过 store.dispatch 方法触发
    doDispatch() {
      this.$store.dispatch('setUserName', '真乖，赶紧关注公众号，组织都在等你~')
    },
    goGithub(index) {
      window.location.href = 'https://github.com/sunniejs/vue-h5-template'
    }
  }
}
</script>
<style lang="scss">
.upload_box{
  display: flex;  
  flex-direction: column;
  align-items: center;
  position: relative;
  
  .id_card{
    margin-top: 20px;
    margin-bottom: 14px;
    width: auto;
    height: auto;
    position: relative;
    .camera_box{
      position: absolute;
      left: 50%;
      top: 50%;
      transform: translateX(-50%) translateY(-50%);
      width: 100%;
      .tips_msg{
        font-size: 15px;
        color: #1CB49D;
        width: 100%;
        font-family: PingFangSC-Medium;
        margin-top: 11px;
      }
    }
  }
  text-align: center;
  margin-top: 25px;
  .upload_text{
    font-size: 14px;
    color: #000;
  }
}
.about-container {
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
}
</style>
