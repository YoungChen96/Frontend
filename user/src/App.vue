<template>
    <Layout>
        <Header>
            <Menu mode="horizontal" :theme='primary'>
                <a class="layout-logo" @click="jump('main')">
                    <img id='logo' src="./assets/SunYet-sen.png">
                    <span id='logo-name'>中山大学图书馆</span>
                </a>
                <div class="layout-nav">
                    <Form ref="formInline" :model="formInline" :rules="ruleInline" inline>
                        <FormItem prop='searchKey' id='search'>
                            <Input v-model="searchKey" placeholder="输入书名、作者、ISBN..." style="width: 200px">
                            </Input>
                            <Button type="primary" @click="handleSubmit('formInline')">search</Button>
                        </FormItem>
                        <a @click="jump('login')">
                            <Avatar style="background-color: green" icon="person" />
                        </a>
                    </Form>
                </div>
            </Menu>
        </Header>
        <router-view></router-view>
        <Footer class="layout-footer-center">Contact us:
            <a href='https://github.com/ProgressOfSAD'>Github</a>
        </Footer>
    </Layout>
</template>

<script>
export default {
  name: "App",
  methods: {
    jump: function(name) {
      switch (name) {
        case "main":
          name = "/";
          break;
        case "login":
          name = "/login";
          break;
        case "community":
          name = "/community";
          break;
        case "search":
          name = "/search";
          break;
        case "user":
          name = "/user";
          if (this.$store.state.userId === "") {
            this.isLogin = true;
            return;
          }
          break;
        case "group":
          name = "/group";
          break;
        default:
          break;
      }
      this.$router.push(name);
    }
  }
};
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
.ivu-layout {
    height: 800px;
}
.layout {
  border: 1px solid #eeeeee;
  /* background: #eeeeee */
  position: relative;
  border-radius: 4px;
  overflow: hidden;
}
.ivu-layout-header {
  background: #f5f7f9;
}
.ivu-layout-sider {
  background: white;
}
.layout-logo {
  width: 200px;
  /* height: 30px */
  /* background: #5b6270 */
  border-radius: 3px;
  float: left;
  position: relative;
  /* top: 15px */
  left: 20px;
}
#logo-name {
  font-size: 15px;
  margin-left: 10px;
  color: grey;
  font-weight: 600;
}
#logo {
  position: relative;
  vertical-align: middle;
  width: 40px;
}
.layout-nav {
  width: 420px;
  margin: 0 auto;
  margin-right: 0px;
}
.layout-footer-center {
  text-align: center;
}
.ivu-form-item-content {
  margin-top: 12px;
}
#search {
    margin-top: 0;
}
</style>

