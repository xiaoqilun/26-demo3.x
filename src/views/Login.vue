<template>
  <div class="login">
    <!-- model属性用于存放表单的数据对象 -->
    <el-form :model="loginForm" class="container" :rules="loginrules" ref="loginRef">
      <el-form-item>
        <img src="../assets/assets/avatar.jpg" alt="头像" class="avatar">
      </el-form-item>
      <el-form-item prop="username">
         <el-input prefix-icon="myicon myicon-user" v-model="loginForm.username"></el-input>
      </el-form-item>
      <el-form-item prop="password">
         <el-input prefix-icon="myicon myicon-key" v-model="loginForm.password" type="password"></el-input>
      </el-form-item>
      <el-form-item>
        <el-button type="primary" class="login-btn" @click="handleLogin">登陆</el-button>
      </el-form-item>
    </el-form>
  </div>
</template>

<script>
export default {
  data () {
    return {
      loginForm: {
        username: '',
        password: ''
      },
      loginrules: {
        username: [
          { required: true, message: '请输入用户名', trigger: 'blur' }
        ],
        password: [
          { required: true, message: '请输入密码', trigger: 'blur' }
        ]
      }
    }
  },
  methods: {
    handleLogin () {
      // console.log('执行登录方法')
      this.$refs.loginRef.validate((isPass) => {
        if (isPass) {
          // 发请求
          console.log('发请求')
        } else {
          // 弹出校验未通过提示信息
          return false
        }
      })
    }
  }
}
</script>

<style lang="scss" scoped>
  .login {
  position: fixed;
  width: 100%;
  height: 100%;
  background-color: #2f4050;

  .container {
    position: absolute;
    left: 0;
    right: 0;
    width: 400px;
    padding: 0px 40px 15px 40px;
    margin: 200px auto;
    background: white;
    .avatar {
      position: relative;
      left: 50%;
      width: 120px;
      height: 120px;
      margin-left: -60px;
      margin-top: -60px;
      box-sizing: border-box;
      border-radius: 50%;
      border: 10px solid #fff;
      box-shadow: 0 1px 5px #ccc;
      overflow: hidden;
    }
    .login-btn {
      width: 100%;
    }
  }
}
</style>
