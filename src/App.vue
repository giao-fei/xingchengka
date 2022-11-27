<template>
 <div class="main">
   <div class="box">
    <div style="text-align: center;">
      <span class="p1">更新于: {{date}}</span>
    </div>
    <span class="p2"><span class="tips">您于7天内到达或途径: </span>{{address}}</span>  
   </div>
 </div>

 <div class="alert" v-show="addressShow">
   <div class="input">
     <input v-model="address" type="text" placeholder="请输入您要显示的城市" /><br>
     <button @click="address!= '' ? addressShow = false : ''">确定</button>
   </div>

 </div>
</template>

<script setup>
  import { parseTime } from '@/utils/ruoyi.js';
  import { ref } from 'vue';
  
  let date = ref('');
  setInterval(() => {
    date.value = parseTime(new Date().getTime(),'{y}.{m}.{d} {h}:{i}:{s}');
  },1000)

  let address = ref('');
  let addressShow = ref(true);
</script>

<style lang="scss" scoped>
  .main {
    min-height: 103.6vh;
    background: url('@/assets/bg.png') no-repeat;
    background-size: 100% auto;
    padding: 0 85px;
  }

  .box {
    position: relative;
    top: 649px;

    .p1 {
      color: #969696;
      letter-spacing: .5px;
      font-size: 28px;
      font-family: 'SourceHanSansCN-Medium';
    }

    .p2 {
      display: block;
      // position: relative;
      padding-top: 420px;
      letter-spacing: .5px;
      font-size: 28px;
      font-family: 'SourceHanSansCN-Medium';
     
      .tips {
        color: #969696;
      }
    }
  }

  .alert {
    overflow: hidden;
    width: 100vw;
    height: 100vh;
    z-index: 99;
    background: rgba(0,0,0,.5);
    position: fixed;
    top: 0;
    left: 0;
    text-align: center;

    .input {
      position: absolute;
      top: 50%;
      left: 50%;
      transform: translate(-50%,-50%);

      input {
        width: 65vw;
        height: 60px;
        padding-left: 10px;
        outline: none;
      }

      input::placeholder {
        padding-left: 10px;
        letter-spacing: 2px;
      }

      button {
        margin-top: 50px;
        padding: 10px 20px;
        border-radius: 10px;
        border: none;
        outline: none;
        font-size: 25px;
      }
    }
  }
</style>
