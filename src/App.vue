<template>
  <div id="app">
    <template v-if="address">
      <h2> {{address}}</h2>
      <h3> {{balance}} LAT</h3>
      <button @click="sendTransaction"> Send Transaction</button>
    </template>
    <template v-else>
      <button @click="connectWallet"> Connect Wallet</button>
    </template>
  </div>
</template>

<script>

import Web3 from "platon-web3/packages/web3";

export default {
  name: 'App',
  data() {
    return {
      address: "",
      balance: "0"
    }
  },
  methods: {
    connectWallet(){
      if(window.platon){
        window.platon.enable().then( accounts => {
          if (accounts && accounts.length > 0) {
            this.address = accounts[0]
            this.getBalance()
          }
        })
      }else{
        alert("Please mathwallet frist!")
      }
    },
    getBalance(){
      let web3 = new Web3(window.platon);
      console.log(web3);
      web3.platon.getBalance(this.address).then(balance => {
        this.balance = web3.utils.fromVon(balance,"lat");
      });
    },
    sendTransaction() {
      let web3 = new Web3(window.platon);
  
      web3.platon.sendTransaction({
          from: this.address,
          to: "lat12rvgpmau0wyx6nnzzjl05gv4c4zxgr72kwg9vg",
          value: web3.utils.toVon(web3.utils.toBN(1),"lat")
        }).then(response => {
          console.log(response);
        }).catch(e => {
          console.log(e);
        });
    }

  },
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
