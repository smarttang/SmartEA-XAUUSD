<img width="693" alt="image" src="https://github.com/user-attachments/assets/61d7a776-970b-4c9e-9d6a-7b26ebcb1c45" />


# 
SmartEA是我开启的一个新的项目，主要面向量化交易做的项目，目前服务于我自己和身边的朋友为主，也都已经实现正盈利，该EA优化了将近60多个版本，从一开始亏损特别多，到现在基本上趋于稳定的状态，过程比较煎熬，且对MQ5的不熟悉编写难度较大，到后面把那本MQ5编写策略的书看完，然后融合自己对MQ5的理解+大模型助力，不断地打磨，才有了SmartEA这个项目，当前策略主要基于XAUUSD的EA交易策略，也是我实盘很久之后才放出来的交易策略，目前需要License才能使用，已经给了一部分小伙伴License，我们也在持续迭代中。同时SmartEA还会针对不同的品种做不同的EA交易策略，同时也会开发Web端平台和SaaS化的量化平台，方便大家私有化部署和直接云端使用。

## 策略说明
1. 目前我正在使用这个策略来做外汇XAUUSD交易，且持续盈利，目前从1000$到19000$，策略比较稳定，且我还在优化。
2. 针对大波动下或大的趋势下，该策略表现最优。
3. 针对震荡，由于历史资金磨损严重，我放弃了震荡行情的参与，后续准备单独写一个震荡行情的EA交易策略。
4. 这个策略有过回测，效果还行，实盘表现我是比较满意的。

## 策略回测
<img width="1395" alt="image" src="https://github.com/user-attachments/assets/24a2d53f-c91a-48f1-93a9-2ffc26a90b84" />
<img width="1394" alt="image" src="https://github.com/user-attachments/assets/1ceb2542-db2a-47d2-a9fa-991757307915" />

## 部分收益截图
### 自己实盘的结果
<img width="1263" alt="image" src="https://github.com/user-attachments/assets/73cd8032-ea4b-4753-a464-d36c20b5bf65" />
<img width="1264" alt="image" src="https://github.com/user-attachments/assets/63bdaa06-989b-4142-ade8-028a6c3e31c8" />
<img width="1263" alt="image" src="https://github.com/user-attachments/assets/1424a4c1-21f2-4c14-b984-c1b82e5e4199" />

### 客户实盘的结果
<img width="1411" alt="image" src="https://github.com/user-attachments/assets/f3048fe7-2ebc-4d94-8ef6-385a3c9293fa" />
<img width="1402" alt="image" src="https://github.com/user-attachments/assets/93a2e12f-3bd0-4b51-8ab5-0dd3a8b76544" />
<img width="1404" alt="image" src="https://github.com/user-attachments/assets/ee4d6235-7ee4-4ad9-a37c-7dbe88bda25b" />
<img width="1406" alt="image" src="https://github.com/user-attachments/assets/29930111-9fa3-4a38-9b77-bcbfa670f152" />
<img width="1405" alt="image" src="https://github.com/user-attachments/assets/422c278e-971a-47d1-ab14-e3ee49562a75" />


## 实际功能
1. 动态止盈：支持动态止盈，根据设定的值进行动态跟随，持续锁定利润。
2. 时区系统：支持时区，不同的时区交易模式切换，动态更新对应的参数，根据时区自适应，实现宽窄幅度的交易策略。
3. 趋势研判：支持动态趋势捕获，获取K线形态进行分析，研判当前趋势的位置，进行开平仓，并且支持斐波那契回撤计算，增加盈利概率。
4. 震荡识别：支持多决策体系震荡识别，通过多指标共振和决策权重算法，进行震荡的判断，包括震荡高低区域、缓冲蓝布的方式进行震荡的交易。
5. 利润/风险预判：支持开仓前盈利和风险预测，盈亏比与风险不成正比不开仓，降低风险订单产出概率，只保留高精度持仓。
6. 拐点算法检测：支持趋势反转拐点检测，在风险来临时，持仓盈利浮盈平仓，在开仓前预判风险，禁止开仓，降低风险。（**目前该算法已成功已出售，在合同保密期**）
7. 小仓位分摊策略：支持浮亏时小仓位密集开仓，分摊亏损，降低止损的余震，并顺应趋势回头盈利。
8. 多品种交易：支持USDJPY、XAUUSD、EURUSD 等 28 个品种的交易，混合开仓、组合开仓。（不支持区块链如BTCUSD等）
9. 消息通知：支持企业微信、钉钉、飞书等机器人通知，报单等。
