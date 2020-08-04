<template>
  <div class="main">
    <div class="loginContent">
      <div class="top">Welcome To My World ! ! !</div>
      <div class="mid">
        <div style="width:70%">
          <input type="text" placeholder="请输入账号" v-model="user" />
          <input type="password" placeholder="请输入密码" v-model="password" />
        </div>
        <div style="width:70%;display:flex;justify-content: space-between;">
          <input style="width:70%" type="text" placeholder="请输入验证码" v-model="checkword" />
          <button class="btn" @click="createCode()">{{checktext}}</button>
        </div>
      </div>
      <div class="und">
        <el-button type="primary" @click="login()" :loading="loading">{{text}}</el-button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      user: "",
      password: "",
      checkword: "",
      checktext: "",
      loading: false,
      text: "登陆"
    };
  },
  mounted() {
    this.createCode();
  },
  methods: {
    createCode() {
      let code = "";
      //设置长度，这里看需求，我这里设置了4
      var codeLength = 4;
      //设置随机字符
      var random = new Array(
        0,
        1,
        2,
        3,
        4,
        5,
        6,
        7,
        8,
        9,
        "A",
        "B",
        "C",
        "D",
        "E",
        "F",
        "G",
        "H",
        "I",
        "J",
        "K",
        "L",
        "M",
        "N",
        "O",
        "P",
        "Q",
        "R",
        "S",
        "T",
        "U",
        "V",
        "W",
        "X",
        "Y",
        "Z"
      );
      //循环codeLength 我设置的4就是循环4次
      for (var i = 0; i < codeLength; i++) {
        //设置随机数范围,这设置为0 ~ 36
        var index = Math.floor(Math.random() * 36);
        //字符串拼接 将每次随机的字符 进行拼接
        code += random[index];
      }
      //将拼接好的字符串赋值给展示的Value
      this.checktext = code;
    },
    login() {
      if (this.user == "") {
        this.$message.error("请输入账号!");
        return;
      } else if (this.password == "") {
        this.$message.error("请输入密码!");
        return;
      } else if (this.checkword == "") {
        this.$message.error("请输入验证码!");
        return;
      } else if (this.checkword.toUpperCase() != this.checktext) {
        this.$message.error("验证码错误!");
        this.createCode();
        return;
      } else if (
        (this.user != "17343030395" || this.user != "13903819240") &&
        this.password != "5201314"
      ) {
        this.$message.error("账号密码错误!");
        return;
      }
      this.text = "正在登陆";
      this.loading = true;
      setTimeout(() => {
        this.$router.push("/index");
      }, 1000);
    }
  }
};
</script>

<style scoped>
* {
  height: 100%;
}
.main {
  width: 100%;
  background-image: url("../assets/timg.jpg");
  position: fixed;
  top: 0;
  left: 0;
}
.loginContent {
  width: 600px;
  height: 500px;
  padding: 0 50px;
  border-radius: 5px;
  background-color: rgba(255, 255, 255, 0.3);
  position: absolute;
  top: 50%;
  right: 50%;
  transform: translate(50%, -50%);
  display: flex;
  align-items: center;
  flex-direction: column;
}
.top {
  width: 100%;
  height: 100px;
  font-size: 25px;
  text-align: center;
  line-height: 100px;
  margin-top: 30px;
}
.mid {
  width: 100%;
  display: flex;
  flex-direction: column;
  align-items: center;
  position: relative;
}
.mid input {
  width: 100%;
  height: 50px;
  border: 1px solid #ccc;
  outline: none;
  border-radius: 5px;
  text-indent: 2em;
  font-size: 16px;
  margin-top: 30px;
  background-color: rgba(255, 255, 255, 0.4);
}
.btn {
  width: 100px;
  height: 50px;
  border: 1px solid #ccc;
  outline: none;
  border-radius: 5px;
  margin-top: 30px;
  font-size: 18px;
  color: #000000;
  position: relative;
  right: -2px;
  background-color: rgba(255, 255, 255, 0.4);
}
.und {
  width: 100%;
  height: 150px;
  text-align: center;
}
.und .el-button {
  width: 80%;
  height: 50px;
}
.el-message {
  height: 100px;
}
</style>>
