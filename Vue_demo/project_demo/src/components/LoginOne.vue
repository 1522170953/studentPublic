<template>
  <div class="login">
    <el-card class="box-card">
      <div slot="header" class="clearfix">
        <span>登录后台管理系统</span>
      </div>
      <el-form label-width="80px" :model="form" ref="form">
        <el-form-item
          label="用户名"
          prop="username"
          :rules="[
            { required: true, message: '请输入用户名', trigger: 'blur' },
            {
              min: 4,
              max: 12,
              message: '输入长度4-10位字符之间',
              trigger: 'blur',
            },
          ]"
        >
          <el-input v-model="form.username"></el-input>
        </el-form-item>
        <el-form-item
          label="密码"
          prop="password"
          :rules="[
            { required: true, message: '请输入密码', trigger: 'blur' },
            {
              min: 6,
              max: 12,
              message: '输入长度6-10位字符之间',
              trigger: 'blur',
            },
          ]"
        >
          <el-input type="password" v-model="form.password"></el-input>
        </el-form-item>
        <el-form-item>
          <el-button type="primary" @click="login('form')">登录</el-button>
        </el-form-item>
      </el-form>
    </el-card>
  </div>
</template>

<script>
export default {
  name: "LoginView",
  data() {
    return {
      form: {
        username: "",
        password: "",
      },
    };
  },
  methods:{
    login(form) {
        this.$refs[form].validate((valid) => {
            if(valid) {
                console.log(this.form);
            }else{
                console.error(this.form);
            }
        })
    }
  }
};
</script>

<style lang="scss" scoped>
.login {
  width: 100%;
  height: 100%;
  position: absolute;
  background: url("../assets/backUrl.jpg");
  background-size: 100%;
  .el-card {
    font-size: 34px !important;
  }
  .el-form {
    padding-right: 35px;
  }
  .box-card {
    width: 450px;
    margin: 200px auto;

    .el-button {
      width: 100%;
    }
  }
}
</style>
