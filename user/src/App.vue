<template>
    <Layout>
      <Header id='header'>
        <Row>
          <Col class='head' span="4"><img @click="jump('login')" id='logo' src="./assets/SunYet-sen.png"></Col>
          <Col class='head' span="4">中山大学图书馆系统</Col>
          <Col class='head' span="4" offset='8'><Icon type="search"></Icon></Col>
          <Col class='head' span="4"><Icon type="person"></Icon></Col>
        </Row>
      </Header>
      <router-view/>
    </Layout>
</template>

<script>
export default {
  name: 'App',
  methods: {
    jump: function (name) {
      switch (name) {
        case 'main':
          name = '/'
          break
        case 'login':
          name = '/login'
          break
        case 'community':
          name = '/community'
          break
        case 'search':
          name = '/search'
          break
        case 'user':
          name = '/user'
          if (this.$store.state.userId === '') {
            this.isLogin = true
            return
          }
          break
        case 'group':
          name = '/group'
          break
        default:
          break
      }
      this.$router.push(name)
    }
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>

<style>
.head {
  height: 100%;
}
#logo {
  height: 15px;
}
#header {
  background-color: #eeeeee;
}
</style>
