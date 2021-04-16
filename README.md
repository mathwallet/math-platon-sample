# For Math Wallet DAPP Developer

## Using Math Wallet PlatON JS API


// Get Accounts
```javascript
const accounts = await window.platon.enable();
```
// Send transaction
```javascript
let web3 = new Web3(window.platon);
web3.platon.sendTransaction({
          from: "lat12rvgpmau0wyx6nnzzjl05gv4c4zxgr72kwg9vg",,
          to: "lat12rvgpmau0wyx6nnzzjl05gv4c4zxgr72kwg9vg",
          value: web3.utils.toVon(web3.utils.toBN(1),"lat")
        })
```

For details, please find the sample in this repo.

### Download Math Wallet 麦子钱包下载

[http://mathwallet.org](http://mathwallet.org)


