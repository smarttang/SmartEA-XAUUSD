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


## 更新日志

### 优化: 2025 - 05 - 20

修复了 IsOscillatingMarket 方法中的震荡判断条件，改进了数据验证和判断逻辑，主要改进包括：

#### 数据验证与安全性加强

  * **添加默认值处理** ：当 InpOscillationBars 设置不合理时使用默认值 10 根 K 线
  * **主动获取更多数据** ：当 K 线数据不足时主动尝试获取更多数据
  * **增加索引有效性检查** ：防止数组越界
  * **增加价格有效性验证** ：确保价格数据有意义
  * **增加点值有效性验证**
  * **确保当前报价有效**

#### 震荡判断逻辑改进

  * **引入价格位置判断** ：引入了价格在范围中的位置判断（pricePosition），增加了判断的维度
  * **综合条件判断** ：使用 smallRange 和 centralPosition 两个条件进行综合判断。当价格区间小时才考虑震荡，但当价格在区间中间位置时更有可能是震荡
  * **增加额外条件** ：当价格区间非常小（小于最大允许区间的 70%）时也认为是震荡

#### 日志输出改进

  * 提供了更详细的震荡判断结果日志，包括价格位置比例、小区间判断、居中位置判断等，便于调试和了解 EA 实际运行情况

这些改进使得震荡判断更加稳健和可靠，尤其是：

  * **避免错误判断** ：不会因为数据不足或无效而导致错误判断
  * **增强识别能力** ：通过多维度的判断标准增强了对震荡行情的识别能力
  * **居中倾向判断** ：在当前报价在区间中居中位置时更倾向于判断为震荡，这符合震荡市场的特征
  * **提供异常日志** ：为异常情况提供了更多日志信息，方便定位问题

### 优化:2025 - 05 - 20

添加了新的早期盈利保护功能。这个新功能可以确保当订单盈利超过 20 点时，会将止损移动到保证至少 10 点盈利的位置。

#### 新增功能的主要内容

  * **添加新函数** ：添加了一个新函数 ApplyEarlyProfitProtection，该函数具有以下功能：
    * 检查订单是否盈利
    * 计算当前价格与开仓价格之间的点差
    * 当点差超过 20 点时，设置止损到保证 10 点盈利的位置
    * 确保新止损符合经纪商的最小距离要求

  * **整合到 ManagePositions 函数中** ：在 ManagePositions 函数中：
    * 首先应用早期盈利保护逻辑
    * 然后再应用基于 K 线的优化移动止盈逻辑

这种策略保证了：

  * **锁定基本盈利** ：一旦订单盈利超过 20 点，立即锁定至少 10 点的盈利
  * **进一步优化止盈** ：随着行情继续向有利方向发展，原有的 K 线移动止盈系统会接管并进一步优化止盈

这样修改后能确保每笔交易一旦有足够的盈利空间就锁定部分盈利，从而提高整体的盈利稳定性。

### 优化:2025 - 05 - 20

增强了早期盈利保护功能，增加了一个智能移动止损系统，现在系统会比较两种策略（基于固定步长和基于 K 线）并选择最优者执行。具体实现如下：

#### 新增三个关键函数

  * **CalculateStepBasedStopLoss** ：计算基于固定步长的移动止损
    * 使用 10 点作为步长单位
    * 随着价格向有利方向移动，止损会按照固定步长上移（多单）或下移（空单）
    * 确保止损价格满足经纪商的最小距离要求

  * **CalculateKLineBasedStopLoss** ：计算基于 K 线高低点的移动止损
    * 提取原有的 K 线移动止损逻辑，生成一个独立的计算函数
    * 如果不满足 K 线移动止损条件，返回 0 表示无效

  * **ApplyIntelligentTrailingStop** ：智能移动止损核心逻辑
    * 首先使用早期盈利保护功能确保至少锁定 10 点利润
    * 然后分别计算两种移动止损方法的结果
    * 根据订单类型选择最优的止损价位：
      * 多单：选择更高的止损位置（越高越能保障更多利润）
      * 空单：选择更低的止损位置（越低越能保障更多利润）

  * **记录策略** ：记录使用了哪种移动止损策略以便调试和分析
