每个块都有奖励，这是产生新货币的唯一途径。

发行曲线：首先有“基本奖励”这个概念，然后根据时间间隔（出块速度）、总供应量、已出总额对其进行调整。

> 对比门罗币，规则更简单了，不再需要根据“中位数”进行调整。

GetBlockReward

```
//TODO trickling code  is note implemented still, but we do NOT require it atleast for another 7-8 years

// the logic is same as cryptonote_basic_impl.cpp

// this file controls the logic for emission of coins at each height
// calculates block reward
```

GetBlockReward\_Atlantis

```
// atlantis has very simple block reward
// since our chain has already bootstrapped
//  FIXME this will not workaround , when already already_generated_coins wraps around
// but we have few years, atleast 6-7 to fix it
```



