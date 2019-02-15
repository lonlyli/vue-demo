<template>
  <div>
    <div v-if="!isReg">
      <div>用户名:</div>
      <input type="text" v-model="username">
      <div>密码:</div>
      <input type="password" v-model="password">
      <div>
        <button @click="login()">登录</button>
        <button @click="reg()">注册</button>
      </div>
    </div>
    <div v-else>
      <div>用户名:</div>
      <input type="text" v-model="username">
      <div>密码:</div>
      <input type="password" v-model="password">
      <div>再次输入密码:</div>
      <input type="password" v-model="repeat">
      <div>
        <button @click="addUser()">确定</button>
        <button @click="cancel()">取消</button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "Login",
  data() {
    return {
      isReg: false,
      username: "",
      password: "",
      repeat: ""
    };
  },
  methods: {
    login() {
      if (
        localStorage.getItem("username") === this.username &&
        localStorage.getItem("password") === this.password
      ) {
        this.$router.push("/home/list");
        this.username = "";
        this.password = "";
      } else {
        alert("用户名或密码不正确！");
      }
    },
    reg() {
      this.isReg = true;
    },
    addUser() {
      if (this.username !== "" && this.password !== "") {
        if (this.password === this.repeat) {
          localStorage.setItem("username", this.username);
          localStorage.setItem("password", this.password);
          // alert('注册成功')
          this.username = "";
          this.password = "";
          this.repeat = "";
          this.isReg = false;
        } else {
          alert("两次密码输入不一致");
        }
      } else {
        alert("用户名和密码不能为空");
      }
    },
    cancel() {
      this.isReg = false;
    }
  }
};
</script>


<style scoped>
</style>
