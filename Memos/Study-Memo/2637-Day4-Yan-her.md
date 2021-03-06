# Week4
## 金融基础知识
### 金融市场与制度

* 分类
  * 直接融资市场（股票、债券）、间接融资市场（银行信贷市场）
  * 一级市场（PE、VC、天使投资，投资于未上市公司的股权）、二级市场
  * 股票市场、债券市场、衍生品市场
* 参与者：银行、券商、保险
* 监管者：央行、证监会、银保监会

金融资产

* 金融资产：现金、股票、债券、外汇、房地产等，也称为投资标的

交易制度（A股市场）

* T+1: 第T天买入的股票，T+1天及以后才能卖出
* 涨跌停：涨跌幅限制为10%，ST股票5%，创业板/科创板20%
* 卖空限制：不允许卖空
* 交易成本：佣金（0.025%），印花税（0.1%）
* 竞价原则：价格优先，时间优先
* 竞价方式：集合竞价、连续竞价
* 上证交易所：沪市主板、科创板
* 深证交易所：深市主板、中小板、创业板、新三板（**不属于A股**）
### 资产定价

无风险收益：中债国债1-3年利率

超额收益：不同情况下指以下的某个概念

* $R-R_f$
* alpha

### 推荐书目

《费希尔·布莱克 革命性金融思想》

## 聚宽
### 本地
### 在线平台

## 量化交易策略开发案例

复习海龟交易法控制头寸的方法

各种细节：

* 盘中停盘、开盘买入能否买入、涨跌停、没钱了……

* 聚宽上可以自动处理，但如果开发自己的交易系统需要考虑

### 股票池：买卖什么

聚宽编程框架

* 启动
  * Initialize()
  * 初始化策略，设置交易成本、滑点等，启动交易实时监测函数run_daily
* 开盘前
  * run_daily(pl_before_market_open, time='before_open')
  * 每个交易日开盘前，自动调用pl_before_market_open函数，准备策略需要的数据
* 盘中
  * run_daily(pl_trade, time='every_bar') #every_bar每一个k线来后都自动调用一次
  * 根据聚宽界面上设定的交易频率，盘中自动调用pl_trade函数，处理交易逻辑
* 收盘后
  * run_daily(pl_after_market_close, time)
  * 每个交易收盘后，自动调用pl_after_market_close, time函数

run_daily的第一个参数是借口函数的定义，可理解为指针

交易逻辑的时间级别：如果选每天，pl_trade只调用一次，日k；如果选每分钟，每个分钟k线都会被调用

交易考虑的因素

* 趋势型策略更关注赔率
* 均值回复型（震荡型）策略还要关注胜率
* 头寸分布在各种策略中都很重要

股票池：构建一个优质股票的集合，但不一定马上买入，而是等优质信号择时

* 选股条件：e.g.上证50中最近突破MA5的股票
* 再平衡：e.g.上证50每半年会调整一次成分股，再平衡周期一般表述为：“X个交易日”
* 容量：e.g.最多要50只（可以不设置容量）

### 择时：什么时候买卖

技术指标

* 均线型
  * MA; EXPMA
* 趋势型
  * MAXD; SAR; ASI; DML
* 摆动型
  * KDJ; RSI; CCI; WR; BOLL
* 能量型
  * OBV; VOL; VR

均线

* 金叉：短时均线上穿长时均线
* 死叉：短时均线下穿长时均线
* 均线策略代码练习2: 日K（每日收盘价的连线）相当于一日均线

## 大作业

交易的6大要素都要考虑进去（注意交易成本）

5分钟介绍不要超时
