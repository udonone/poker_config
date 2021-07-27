# Poker Config
## 说明
* 共享文档，开发阶段会及时更新
  * networks/testnet.json 合约地址，以及一些币种的基本信息
  * networks/testnet_abi.json 前后端需要的abi定义

* 暂时的说明
  * 通过 Venus testnet(https://testnet.venus.io/faucet) 环境，可以领取相关币种
  * 调用Deposit方法前，要先对币种approve
  * 前端主要是调用Deposit\Withdraw\WithdrawAll 三个业务方法，来实现存取
  * 暂时支持的是BUSD和USDC，它们的pid分别为0和1
  * Seed Token会在每次Withdraw时发放

