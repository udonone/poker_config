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
  * Seed Token会在每次投出、赎回时发放

* 前端显示使用到的接口
  * farm.userInfo[pid][user address]
    * [0] shares
    * [1] rewardDebt (已发放的奖励)
    * [2] 在投余额
  * farm.poolInfo[pid]
    * [0] 投的币种
    * [1] 一般为100的倍数，用于Seed发放时的分配比例
    * [2] accSeedPerShare
    * [3] 策略机的地址
    * [4] 池子的余额
  * poolLength 有几个池子，pid从0开始
  * totalAllocPoint 总的比例基数，其实等于每个池子的比例之合
  * 用户每个池子的在投收益 = user.shares * pool.accSeedPerShare/(10**12)-user.rewardDebt

* 服务端指定用户发放seed
  * farm.sendSeed(address _to, uint256 _amount)
