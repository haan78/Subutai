<template>
  <div class="container">
    <div class="main">
      <div class="header">
        <h2 class="logo">LOGO HERE</h2>
      </div>
      <div class="body">
        <el-card>
        <Login v-if="com == 'login'"></Login>
        <Forgot v-if="com == 'forgot'"></Forgot>
        <Register v-if="com == 'register'"></Register>
        <Activate v-if="com == 'activate'"></Activate>
        <PassReset v-if="com == 'reset'"></PassReset>
        
      </el-card>
      </div>
      

      <div class="footer">
        <div class="links">
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import "element-plus/lib/theme-chalk/index.css";
import Login from "./Login";
import Forgot from "./Forgot";
import Register from "./Register";
import Activate from "./Activate";
import PassReset from "./PassReset";
export default {
  components: { Login, Forgot, Register, Activate, PassReset },
  data() {
    return {
      com: "login"
    };
  },
  created() {
    //console.log(document.cookie);
    //console.log(this.$subutai.data());
    this.com = (window.__DATA__ && window.__DATA__.com ? window.__DATA__.com : "login");
  },
  methods: {
    get() {
      let self = this;
      self.$subutai.ajax("/ajax/server", null, (response) => {
        console.log(response);
      });
    },
    request(req) {
      req.send("/mongo", { name: "Selam", id: 213 }, (response, type) => {
        console.log(response);
        console.log(type);
      });
    },
  },
};
</script>

<style lang="scss">
html, body {
    height: 100%;
    background: cornflowerblue;
}
body {
    margin: 0;
}
#app {
  height: 100%;
}
.container {
  height: 100%;
  display: flex;
  align-items: center;
  justify-content: center;

  .main {
    max-width: 60%;
    min-width: 30%;
    .header {
      text-align: center;
      padding-bottom: 1em;
    }

    .footer {
      text-align: center;
      padding-top: 2em;

      a {
        color: #FFF;
        text-decoration: none;
        padding: 1.5em;
        &:hover {
          color: cyan;
        }        
      }
    }
  }
}
</style>
