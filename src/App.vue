<template>
  <div id="app">
    <button @click="handleLogin">Login</button>
    <button @click="handleWindowLogin">windowLogin</button>
    <button @click="handleTrackSession">trackSession</button>
    <button @click="handleLogout">Logout</button>
  </div>
</template>

<script>
import AuthingSSO from "./lib/index";
export default {
  name: "app",
  mounted() {
    // oidc
    // this.auth = new AuthingSSO({
    //   appId: "5ceb6fecf218f50689b72c1c",
    //   appType: "oidc",
    //   appDomain: "oidc1.localtest.com",
    //   nonce: 113,
    //   timestamp: Date.now(),
    //   dev: true
    // });
    // oauth
    window.auth = this.auth = new AuthingSSO({
      appId: "5e3a3b2315a0b8398cdaaa0e",
      appType: "oidc",
      appDomain: "test.littleimp.cn",
      scope: 'openid profile email phone offline_access',
      state: 'testgood',
      nonce: 113,
      timestamp: Date.now(),
      dev: true
    });
    // saml sp
    // this.auth = new AuthingSSO({
    //   appId: "5cefc1148e241e66339fd601",
    //   appType: "saml",
    //   appDomain: "sp1.localtest.com",
    //   nonce: 113,
    //   timestamp: Date.now(),
    //   dev: true
    // });
    // saml idp
    // this.auth = new AuthingSSO({
    //   appId: "5cefc0408e241ed5759fd600",
    //   appType: "saml",
    //   appDomain: "idp1.localtest.com",
    //   nonce: 113,
    //   timestamp: Date.now(),
    //   dev: true
    // });
    console.log(this.auth)
  },
  methods: {
    async handleTrackSession() {
      // let res = await this.auth.login()
      let res = await this.auth.trackSession()
      alert(JSON.stringify(res, null, 4))
      console.log(res)
    },
    async handleLogin() {
      this.auth.login()
    },
    handleWindowLogin() {
      this.auth.windowLogin()
    },
    async handleLogout() {
      let res = await this.auth.logout()
      alert(JSON.stringify(res))
      console.log(res)
    }
  }
};
</script>

<style>

</style>
