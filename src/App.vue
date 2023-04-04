

<template>
  <div>
    <button @click="loginMeta">Login Metamask</button>
    <h6 v-if="wallet">{{ wallet }}</h6>
    <h6>{{ info }}</h6>
    
  </div>

</template>



<script>

export default{
 data() {
    return {
      login: false,
      info:'',
      wallet:""
    }
  },
  methods: {
    async loginMeta() {
      const user = await ethereum.request({ method: 'eth_requestAccounts' });
      this.wallet = user[0]
    }
  },

  mounted () {
    if (typeof window.ethereum === 'undefined') {
       this.info = 'MetaMask is not install!'
    }
  },
}

 

</script>

<style scoped>
.logo {
  height: 6em;
  padding: 1.5em;
  will-change: filter;
  transition: filter 300ms;
}
.logo:hover {
  filter: drop-shadow(0 0 2em #646cffaa);
}
.logo.vue:hover {
  filter: drop-shadow(0 0 2em #42b883aa);
}
</style>
