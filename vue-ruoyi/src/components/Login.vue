<template>
  <div class="login">
    <div class="bg-image">
       <img src="../assets/images/login-background.jpg" alt="" class="imgSrc">
    </div>
     <el-form :model="ruleForm" status-icon :rules="rules" ref="ruleForm"  class="login-from">
       <h2 class="title">若依后台管理系统</h2>
       <!-- 账号 -->
       <el-form-item  prop="username">
        <el-input type="text" v-model="ruleForm.username" placeholder="账号" autocomplete="off"></el-input>
      </el-form-item>
      <!-- 密码 -->
      <el-form-item  prop="password" class="el-input">
        <!-- 回车触发聚焦 
        用户框里放：@keyup.enter.native="keyupClick";
        密码框里放:：ref="mima"
        -->
        <el-input type="password" v-model="ruleForm.password" autocomplete="off" placeholder="密码"   @keyup.enter.native="handleLogin" class="input"></el-input>
      </el-form-item>
      <!-- 验证码 -->
      <el-form-item  prop="code">
        <el-input v-model="ruleForm.code" autocomplete="off" placeholder="验证码" style="width: 63%" 
        @keyup.enter.native="handleLogin"></el-input>
        <div class="login-code">
          <img :src="codeUrl" @click="getCode" class="login-code-img" alt="">
        </div>
      </el-form-item>
      <!-- 复选框 -->
      <el-checkbox v-model="ruleForm.rememberMe" style="margin:0px 0px 25px 0px;">记住密码</el-checkbox>
      <!-- 登录按钮 -->
      <el-form-item style="width:100%;">
        <el-button
          :loading="loading"
          size="medium"
          type="primary"
          style="width:100%;"
          @click.native.prevent="handleLogin"
        >
          <span v-if="!loading">登 录</span>
          <span v-else>登 录 中...</span>
        </el-button>
      </el-form-item>
     </el-form>
     <div class="el-login-footer">
       <span>Copyright © 2018-2021 ruoyi.vip All Rights Reserved.</span>
     </div>
    </div>
</template>

<script>
export default {
  name: "Login",
  data() {
    return {
      codeUrl:"",
      ruleForm: {
        username: "admin",
        password: "admin123",
        rememberMe: false,
        code: "",
        uuid: ""
      },
      rules: {
        username: [ { required: true, trigger: "blur", message: "用户名不能为空" }],
        password: [{ required: true, trigger: "blur", message: "密码不能为空" }],
        code: [{ required: true, trigger: "change", message: "验证码不能为空" }],
      },
      loading: false
    };
  },
 
  created() {
    this.getCode();
  },
  
  methods: {
    //验证码
    getCode() {
      
    },
    // 校验
    handleLogin(event) {
      console.log(event);
      this.refs.ruleForm.validate(valid =>{

      })
    }
  }
};
</script>

<style scoped>
.bg-image {
  width: 100%;
  height: 100%; /**宽高100%是为了图片铺满屏幕 */
  z-index: -1;
  position: fixed;
  top: 0px; /*这里是设置与顶部的距离*/
  left: 0px; /*这里是设置与左边的距离*/
  bottom: 0px;
  right: 0px;
}
.imgSrc {
  width: 100%;
}
.title{
  margin: 0 auto 30px auto;
  text-align: center;
  color:#707070;
}
.login-from{
  border-radius: 6px;
  background: #ffffff;
  width: 400px;
  padding: 25px 25px 5px 25px;
  position:absolute;
  top:calc(50% - 200px);
  left:calc(50% - 200px);
}
.login-from .el-input{
  height: 38px;
}
.el-input input{
  height: 38px;
}
.login-code{
  display: inline-block;
}
.el-login-footer{
  height: 40px;
  line-height: 40px;
  position: fixed;
  bottom: 10px;
  width: 100%;
  text-align: center;
  font-family: Arial;
  color: #fff;
  font-size: 12px;
  letter-spacing: 1px;
}

</style>