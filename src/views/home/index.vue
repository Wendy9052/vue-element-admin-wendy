<!-- home -->
<template>
  <div class="index-container">
    <top-bar :title="title"></top-bar>
    <div class="step_box">
      <!-- 线 -->
      <div class="line"></div>
      <!-- 3个圆点 -->
      <div class="dot_box">
        <div class="dot dot_active">
        </div>
        <div class="dot"></div>
        <div class="dot"></div>
      </div>

      <!-- 3个文字信息 -->
      <div class="text_box">
        <div class="text">基础信息</div>
        <div class="text">身份证件</div>
        <div class="text">签署协议</div>
      </div>
    </div>

    <!-- 输入信息 -->
    <div class="msg_box">
      <ul>
        <li>
          <div class="msg_title"><span>*</span>姓名</div>
          <input type="text" value="" placeholder="请输入您的姓名">
        </li>
        <li>
          <div class="msg_title"><span>*</span>身份证号</div>
          <input type="text" value="" placeholder="请输入您的身份证号">
        </li>
        <li>
          <div class="msg_title"><span>*</span>手机号码</div>
          <input type="text" value="" placeholder="请输入您的手机号码">
        </li>
        <li>
          <div class="msg_title"><span>*</span>银行卡号</div>
          <input type="text" value="" placeholder="请输入您的银行卡号">
        </li>
        <li>
          <div class="msg_title"><span>*</span>开户行</div>
          <input type="text" value="" placeholder="请输入您的开户行">
          
        </li>
      </ul>
    </div>
    <van-field
      v-model="fieldValue"
      is-link
      readonly
      label="地区"
      placeholder="请选择所在地区"
      @click="show = true"
    />
    <van-popup v-model="show" round position="bottom">
      <van-cascader
        v-model="cascaderValue"
        title="请选择所在地区"
        :options="options"
        @close="show = false"
        @finish="onFinish"
      />
    </van-popup>
    <div class="tips_msg">
      <div class="tips_icon">!</div>
      <div class="tips_text">身份信息及银行卡信息会做公安系统验真</div>
    </div>

    <div class="btn_box">
      <button class="pre_step">返回</button>
      <!-- <router-link to="/about"> -->
        <button class="next_step" @click="nextStep">下一步</button>
      <!-- </router-link> -->
    </div>
  </div>
</template>

<script>
// import { XInput,Group } from 'vux'
// import { PopupPicker } from 'vux'
import Vue from 'vue';
import { Cascader,Field  } from 'vant';

// Vue.use(Cascader);
// Vue.use(Field);

import topBar from '@/components/topBar'
export default {
  data() {
    return {
      title:"生命绿洲众包信息注册",
      show: false,
      fieldValue: '',
      cascaderValue: '',
      // 选项列表，children 代表子选项，支持多级嵌套
      options: [
        {
          text: '浙江省',
          value: '330000',
          children: [{ text: '杭州市', value: '330100' }],
        },
        {
          text: '江苏省',
          value: '320000',
          children: [{ text: '南京市', value: '320100' }],
        },
      ],
    }
  },
  components:{
    topBar,
    // Cascader,
    Field 
  },

  computed: {},

  mounted() { },

  methods: {
    nextStep(){
      
    },
    // 全部选项选择完毕后，会触发 finish 事件
    onFinish({ selectedOptions }) {
      this.show = false;
      this.fieldValue = selectedOptions.map((option) => option.text).join('/');
    },
  }
}
</script>
<style lang="scss" scoped>
.index-container {
  .btn_box{
    display: flex;
    justify-content: space-evenly;
    align-items: center;
    box-shadow: 0px -1px 0px 0px #ccc;
    padding: 8px 0;
    position: fixed;
    left: 0;
    right: 0;
    bottom: 50px;
    
    .pre_step{
      height: 44px;
      width: 30%;
      border: 0.5px solid rgba(28, 180, 157, 1);
      border-radius: 22px;
      background-color: rgba(255, 255, 255, 1);
      color: rgba(28, 180, 157, 100);
      font-size: 15px;
      text-align: center;
      font-family: PingFangSC-Medium;
    }
    .next_step{
      height: 44px;
      width: 60%;
      background-color: rgba(28, 180, 157, 1);
      border-radius: 22px;
      color: rgba(255, 255, 255, 100);
      border: 0.5px solid rgba(28, 180, 157, 1);
    }
  }
  .tips_msg{
    display: flex;
    align-items: center;
    margin-top: 24px;
    margin-left: 15px;
    height: 16px;
    .tips_text{
      color: #FF6145;
      margin-left: 5px;
      font-size: 13px;
    }
    .tips_icon{
      width: 16px;
      height: 16px;
      background: #FF6145;
      color: #fff;
      display: flex;
      justify-content: center;
      align-items: center;
      border-radius: 50%;
    }
  }
  .msg_box{
    padding: 0 10px;
    ul{
      // background: pink;
      li{
        background: #fff;
        width: 100%;
        border-bottom: 1px solid #ccc;
        display: flex;
        justify-content: space-between;
        align-items: center;
        .msg_title{
          font-size: 15px;
          width: 100px;

          span{
            color: #F22B2E;
            margin-right: 3px;
          }
        }
        select{
          height: 55px;
          width: 100%;

          flex-grow: 1;
          // border: none;
          // appearance:none;
          // -moz-appearance:none;
          // -webkit-appearance:none;


        }
        input{
          // border: none;
          // width: 100%;

          height: 55px;
          width: 100%;
          border: none;
          flex-grow: 1;
        }
        input::-ms-input-placeholder{
          text-align: right;
          font-size: 15px;
          color: rgba(0, 0, 0, 0.4);
        }
        input::-webkit-input-placeholder{
          text-align: right;
          font-size: 15px;
          color: rgba(0, 0, 0, 0.4);
        }
      }
    }
  }
  .step_box{
    height: 68px;
    background: #1CB49D 1%;
    padding-top: 10px;
    .text_box{
      display: flex;
      justify-content: space-between;
      padding: 6px 18px;
      .text{
        font-size: 14px;
        color: #fff;
      }
    }
    .line{
      width: 75%;
      height: 4px;
      background: #fff;
      margin: 15px auto 0;
    }
    .dot_box{
      margin: 0 auto;
      // background: pink;
      width: 78%;
      display: flex;
      display: flex;
      justify-content: space-between;
      .dot{
        width: 16px;
        height: 16px;
        background: #fff;
        border-radius: 50%;
        margin-top: -10px;
      }
      .dot_active{
        width: 12px;
        height: 12px;
        background: #FFB253;
        border: 8px solid #fff;
        border-radius: 50%;
        margin-top: -16px;
      }
    }

  }
}
</style>
