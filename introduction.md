# FUND OF FUNDS AMM-BASED STRATEGIES

# Introduction

**The use-case:** Yearn Lazy Ape (YLA) Pool composition is composed of Yearn Vaults LP Shares and acts as *Fund-of-Funds structured investment product*

**Fund Of Funds strategy:** a strategy based on holding a basket of shares of third-party investment funds[1].

In web3.0 Vaults are automated fund management strategies:

![](https://i.imgur.com/vGk3PgO.png)

**Team:** Vasily Sumanov, discord Vasily Sumanov | PowerPool#8723
*[Balancer Simulations Group](https://discord.gg/Kf3VPAVh8j)*

# Research question & tasks

**Research question:** compare different FOF strategies applied to YLA

**Tasks:**
1. Create building blocks aka "Fund of Funds strategies lego" on Python
2. Test strategies and their combinations on real on-chain data (30 days period)
3. Compare outcomes & make conclusions

# The simulation methodology, input data, and metrics

**Key metric:** absolute profit (in USDC) generated over a period by the YLA Pool (can be presented as APR)

> Continiously allocate YLA to set of Vaults to maximize returns

**The input data:** only **TVL** and **SharePrice** (how many USDC you can get by redeeming this Yearn Vault token)
![](https://i.imgur.com/SAThJVv.png)


**Simulation methodology**

The YLA composition is updated every DELTA steps using certain strategy.


**1. Basic Fund-of-Funds strategies:**

1.1. TVL-based strategy. Share of vault = TVLi/sum(TVLi)
1.2. dTVL or TVL derivative. Share of vault = dTVL_i/sum(TVLi)
1.3. dSharePrice or rate of growth. Share of vault = dSP_i/sum(dSP_i)

An example of transaction updating the basket composition **(TVL-based strategy)**: https://etherscan.io/tx/0x8ef7d7db5c255a1aa6841b7a91182b74b84b305ea2fe6613347c84ecb37ed87e

2. Combination of "FOF Lego" strategies, including optimization of A,B,C parameters (A+B+C=1, shares of capital allocation)


# Results

**Strategy 1 (TVL):** 14.96% APY, $124.8k profit
![](https://i.imgur.com/urxfaNl.png)

**Strategy 2 (1/3 TVL, 1/3 dTVL, 1/3 dSharePrice):** 15.34% APY, ~$128k profit
![](https://i.imgur.com/ZOXbMJ5.png)

**Strategy 3 (dSharePrice):** 14.25% APY, $118.9k
![](https://i.imgur.com/E7K7Cfp.png)

**Comparison of strategies**:
![](https://i.imgur.com/kn40tyD.png)



# Github

https://github.com/VasilySumanov/FundOfFunds

# Learnings and conclusions

**Conclusion 1:** by using only two metrics - TVL and Share Price it is possible to create a lot of strategies
**Conclusion 2:** dSharePrice looks like most efficient approach
**Conclusion 3:** Without limits almost all capital will be in USDN since this Vault is "champion" according to all three strategies - TVL, dTVL, dSharePrice

# Future Work

We plan to Migrate to Balancer v2 StableSwap pool and conducting research at this point.

# Resources:
[1] https://en.wikipedia.org/wiki/Fund_of_funds

[2] https://finematics.medium.com/what-are-yearn-vaults-eth-vault-explained-3def4f77b59d

[3] https://medium.com/powerpool/yearn-lazy-ape-launches-c183703bb942
