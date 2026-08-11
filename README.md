# ETFOptionHandler

本代码库演示了如何通过akshare获取实时的ETF期权价格，如何计算期权的隐含波动率，如何计算策略组合的希腊字母（greeks），并且这些计算都是基于实时数据。

## 功能概述

- 获取指定标的ETF的实时期权合约信息
- 查询期权合约的实时价格和希腊字母值
- 计算期权的隐含波动率
- 可视化隐含波动率曲线
- 如何实时计算策略组合的希腊字母（greeks）

## 项目结构

```
ETFOptionHanlder/
├── Contracts.py           # 获取ETF期权合约信息的主要模块
├── ImpliedVolatility.py   # 隐含波动率计算和可视化模块
├── Portfolio.py           # 实时计算策略组合的希腊字母（greeks）模块
├── requirements.txt       # 项目依赖
└── util/                  # 工具函数
    ├── option_calculation.py  # 基本的期权计算函数
    └── util.py                # 通用工具函数
```

## 主要文件说明

### Contracts.py

该模块演示了如何获取ETF期权合约的基本信息，包括：
- 获取正在交易的期权月份列表
- 查询期权合约的行权日
- 获取特定月份的认购/认沽期权合约列表
- 获取单个期权合约的实时价格和希腊字母值
- 获取标的ETF的实时价格

### ImpliedVolatility.py

该模块演示了如何计算和可视化期权的隐含波动率：
- 获取期权合约的实时价格数据
- 使用二分法计算隐含波动率
- 绘制隐含波动率曲线

### Portfolio.py

该模块演示了如何实时计算策略组合的希腊字母（greeks）：
- 跨式策略（Straddle）
- 宽跨式策略（Strangle）
- 牛市价差策略（Spread）

### util/option_calculation.py

包含期权计算的核心函数：
- 计算看涨期权价格（Black-Scholes模型）
- 计算看跌期权价格（Black-Scholes模型）
- 使用二分法迭代计算隐含波动率

### util/util.py

包含通用工具函数：
- 修复matplotlib中文字体显示问题
- 预定义的ETF期权标的列表

## 依赖项

- akshare>=1.9.0 - 用于获取金融数据
- pandas>=2.0.0 - 数据处理
- matplotlib>=3.7.0 - 数据可视化
- scipy>=1.10.0 - 科学计算
- numpy>=1.24.0 - 数值计算

## 使用方法

### 安装依赖

```bash
pip install -r requirements.txt
```

### 获取期权合约信息

```bash
python Contracts.py
```

### 计算并可视化隐含波动率

```bash
python ImpliedVolatility.py
```

### 计算策略组合的希腊字母（greeks）

```bash
python Portfolio.py
```

## 支持的ETF标的

目前支持的ETF期权标的包括：
- 510050（上证50ETF）
- 510300（沪深300ETF(沪)）
- 159919（沪深300ETF(深)）
- 510500（中证500ETF(沪)）
- 159922（中证500ETF(深)）
- 588000（科创50ETF）
- 588080（科创50ETF易方达）
- 159915（创业板ETF）
- 159901（深证100ETF）

## 注意事项

- 本代码库使用的数据接口基于akshare，请注意接口可能会发生变化
- 隐含波动率计算基于Black-Scholes模型，适用于欧式期权
- 无风险利率默认为1.8%（年），实际使用时可根据市场情况进行调整






## English Description

ETFOptionHandler demonstrates how to retrieve real-time Chinese A-share ETF option data with AkShare, calculate option implied volatility, and calculate portfolio Greeks using live market data.

### Overview

- Retrieve real-time option contract information for specified ETF underlyings
- Query real-time option prices and Greeks
- Calculate option implied volatility
- Visualize implied-volatility curves
- Calculate Greeks for option strategy portfolios in real time

### Project Structure

```text
ETFOptionHanlder/
├── Contracts.py           # Retrieves ETF option contract information
├── ImpliedVolatility.py   # Calculates and visualizes implied volatility
├── Portfolio.py           # Calculates portfolio Greeks in real time
├── requirements.txt       # Project dependencies
└── util/                  # Utility functions
    ├── option_calculation.py  # Core option-calculation functions
    └── util.py                # General utility functions
```

### Main Files

#### Contracts.py

Retrieves basic ETF option contract information, including:

- Currently trading option expiration months
- Option expiration dates
- Call and put option contract lists for a specified month
- Real-time prices and Greeks for individual option contracts
- Real-time prices for underlying ETFs

#### ImpliedVolatility.py

Calculates and visualizes option implied volatility:

- Retrieves real-time option price data
- Calculates implied volatility using the bisection method
- Plots implied-volatility curves

#### Portfolio.py

Calculates Greeks for option strategy portfolios in real time:

- Straddle strategies
- Strangle strategies
- Bull spread strategies

#### util/option_calculation.py

Provides core option-calculation functions:

- Prices call options with the Black-Scholes model
- Prices put options with the Black-Scholes model
- Iteratively calculates implied volatility using the bisection method

#### util/util.py

Provides general utility functions:

- Fixes Chinese font rendering in Matplotlib
- Defines supported ETF option underlyings

### Dependencies

- akshare>=1.9.0 - Financial data retrieval
- pandas>=2.0.0 - Data processing
- matplotlib>=3.7.0 - Data visualization
- scipy>=1.10.0 - Scientific computing
- numpy>=1.24.0 - Numerical computing

### Usage

#### Install Dependencies

```bash
pip install -r requirements.txt
```

#### Retrieve Option Contract Information

```bash
python Contracts.py
```

#### Calculate and Visualize Implied Volatility

```bash
python ImpliedVolatility.py
```

#### Calculate Portfolio Greeks

```bash
python Portfolio.py
```

### Supported ETF Underlyings

- 510050 (SSE 50 ETF)
- 510300 (CSI 300 ETF, Shanghai)
- 159919 (CSI 300 ETF, Shenzhen)
- 510500 (CSI 500 ETF, Shanghai)
- 159922 (CSI 500 ETF, Shenzhen)
- 588000 (STAR 50 ETF)
- 588080 (STAR 50 ETF, EFANGDA)
- 159915 (ChiNext ETF)
- 159901 (SZ100 ETF)

### Notes

- Data is obtained through AkShare interfaces, which may change over time.
- Implied volatility is calculated with the Black-Scholes model and is intended for European options.
- The default annual risk-free rate is 1.8%; adjust it to reflect market conditions when needed.
