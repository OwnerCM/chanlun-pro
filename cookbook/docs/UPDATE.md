# 更新日志

---

### 2025-06-28

* 新增相似股票选股，选股脚本 `script/crontab/xuangu_by_same.py`
* 升级 Tradingview 到最新版本
* 新增多均线指标 @东
* 修复 bug

### 2025-06-20

* 增加TV图表自定义指标（海底捞月/超买超卖/发财线/弘历背离王/龙头趋势/黑马/抄底必备/成交量/弘历飞天线） 贡献者 @东
* 监控列表，增加刷新按钮
* 修复BUG

### 2025-06-11

> 数据库变更语句：

```
ALTER TABLE `cl_alert_task`
	ADD COLUMN `check_idx_ma_info` VARCHAR(200) NULL DEFAULT NULL COMMENT '检查指数的均线' AFTER `check_xd_mmd`,
	ADD COLUMN `check_idx_macd_info` VARCHAR(200) NULL DEFAULT NULL COMMENT '检查指数的MACD' AFTER `check_idx_ma_info`;
```

> 关于沪深股票行业与板块的获取方式，项目中提供了两种方式：    
> 1. 通过 Akshare 抓取东方财务网页内容，获取行业、板块信息，有可能会被封禁，需要手动打开页面进行验证才可继续使用
> 
> 2. 通过设置 config.py 配置的 TDX_PATH 本地通达信安装路径，读取通达信文件获取行业与概念；（推荐使用）

* 沪深市场，网页增加行业&概念板块查看
* 提醒设置，增加指标的监控，包括均线与macd指标的上穿下穿提醒
* 重新梳理获取行业与概念板块的代码
* 优化页面显示提醒消息的列表展示


### 2025-05-22

> config.py 配置文件变更，新增 OPENROUTER_AI_KEYS OPENROUTER_AI_MODEL 配置

* 优化前端部分功能的操作体验
* 优化周期合成方法性能
* 新增 Openrouterai 模型调用支持
* 优化 AI 分析提示词与页面展示
* 升级 Tradingview 到最新版本
* 重构前端代码，按功能拆分 js 代码


### 2025-05-09

* 新增纽约期货市场
* 数字货币历史行情获取优化
* 数字货币可以根据交易所返回小数点，tv自动进行显示调整
* 前端 TV 货期历史行情优化，后续更新只返回最新数据，减少后续网络请求流量
* 交易所获取所有代码，去除无效的代码数据（数字货币/qmt）
* 沪深TDX行情，支持北京交易所数据（将代码硬编码到代码中）
* 其他BUG修复


### 2025-02-12

* 新增中枢重叠选项（可选择前三段，还是所有段 作为中枢重叠区间）
* 数字货币时间，根据用户所在时区进行显示与保存
* 优化 install_windows.bat 安装脚本
* 优化 run.bat 启动 web 服务的脚本
* 升级 layui 前端框架版本
* 其他BUG修改


### 2025-02-08

> `config.py`  配置文件中新增 `AI_TOKEN` `AI_MODEL` 变量设置

* 新增AI缠论分析助手
* 其他BUG修改

### 2025-01-20

> `config.py`  配置文件中新增 `EXCHANGE_FX = 'tdx_fx'` 变量设置

* 新增外汇市场，并添加 通达信外汇 行情数据 @Tim Lee
* 前端页面可以显示或隐藏右侧菜单栏

### 2025-01-05

* 回测支持期货保证金计算方式    
* 更新手续费计算方式    
* 优化回测盈亏计算方式    
* 优化前端搜索框，初始显示之前搜索选项  @吕晓东   

### 2024-12-17

* 回测：支持期货回测交易计算（按照设置的保证金比例与手续费进行计算）
* K线合成优化


### 2024-10-18

* 缠论计算
    * 重构线段计算方法，新增更多可选选项设置
    * 优化计算性能，提升 20-80%（不同的数据量/配置提升不同）
    * 定制化配置项：判断趋势时，是否验证中枢级别的开关

* 修改自动创建数据库表的字符集
* 项目文档更新（缠论配置项）
* TV版本升级
* 其他BUG修改


### 2024-08-09

* 新增数字货币现货市场
* 新增web页面登录验证功能
* 修复 BUG

### 2024-06-12

* 添加 python 3.11 版本的支持
* 新增 苹果M系列芯片的解决方案
* 回测框架，优化信号模式转交易模式的性能
* 前端框架版本更新
* 其他BUG修改

### 2024-05-31

* 回测框架
    * 支持不同平仓类型的记录，后续可通过程序计算，选择最优的平仓条件
    * 修改回测交易中记录的数据结构（对之前的不做兼容）
    * 新增 order_draw_tv_mark 方法，可将订单信息标记在 前端 tv 图表中
    * 新增 signal_to_trade.py 文件，可将信号模式的回测结果，转换成实际交易模式

* 修复 TDX 沪深行情当日分钟数据异常
* 升级 tv 图表为最新版本

### 2024-03-24

> pip install pyfolio-reloaded

* check_end.py 检查环境脚本，针对于 Redis 与 Mysql 不是必须检查项
* 交易回测模式，增加 pyfolio 结果展示，方法 （result_by_pyfolio）

### 2024-03-19

* 缠论计算：
    * bug修复，针对于行情日期不断延后的问题
    * macd 采用全量重新计算的方式

* 前端样式调整
* 回测结果图表优化
* 回测新增信号过滤模块，可根据实际策略进行使用
* 数字货币行情合并问题，关于 utc 时间的处理
* 沪深A股行情概念信息，数据由同花顺修改为东方财富
* stock_bkgn.py 新增获取板块行情的方法，由 akshare 提供

### 2024-01-24

* 图表布局、指标保存方式重新设计
* 美股行情获取修改增量更新
* 其他bug 修复。

### 2023-12-25

> pip install lark-oapi
>
> config.py 新增 飞书key的设置项

* 钉钉旧版的消息推送接口已经停止申请，项目中更新使用飞书的消息接口
* Bug 修复

### 2023-12-22

> 更新需要更新 config.py 文件   
> 
> 需要安装 sqlalchemy； pip install sqlalchemy

* 配置文件修改

        新增 DATA_PATH，可以自己定义数据文件的存储位置
        项目数据保存路径，如果以 . 开头，则保存到 home 目录，否则按照设置目录来

        新增 DB_TYPE，可以指定使用的数据库，支持 sqlite 和 mysql

        REDIS_HOST 可以不用设置，改为非必须的

        ZX 自选配置删除，改为在 web 页面中自行管理

* 修改数据库，使用 sqlalchemy ORM，可以使用 sqlite 或 Mysql 数据库，可根据自己需求进行切换
* 修改数据库中的 各个行情表名，具体可参看 db.py:177 行内容
* 升级 ccxt 到最新的 4.1.95 版本
* 通达信的美股、港股，使用 AKShare 获取复权因子，计算复权后的行情数据
* 其他bug修复与优化

* WEB功能更新
    * 新增自选组管理功能
    * 自选组可进行导入导出操作
    * 完善行情监控设置
    * 可在 web 中进行选股操作（需要在 python 源码中进行相应的配置）


### 2023-11-28

* 升级Pyarmor加密方法，使用新的授权方式
* 优化 TV 画图效率

### 2023-10-15

* 缠论计算修改
    * 新增个人定制，缠论缺口
    * 分型计算优化
* 回测 run 方法增加回调方法参数
* chanlun_chart web 项目，tv 图表配置增加分型显示选项
* tv 图表版本更新

### 2023-10-02

        config.py 配置文件中，新增 TDX_PATH 参数配置

* 缠论计算修改
    * 缠论K线的开盘收盘根据包含方向，修改为高低价格
    * 重新整理了缠论K线合并的方法
    * 次高低成笔，加入K线数量判定
* 新增通过通达信本地安装程序，获取沪深A股的行业与概念信息（需要在 config.py 中配置通达信的安装路径）
* 数字货币行情数据库表名前缀修改为 currency
* 通达信行情服务器异常，程序重新自动选择最优服务器进行重试
* 行情数据合并的时间处理修改
* rd.py 增加 add_code_marks 方法，可以再  tv 图表的时间轴显示自定义标记

### 2023-08-13

* 自选操作新增：颜色设置、置顶、置底操作（右键进行操作）
* 回测代码优化与BUG修复
* 文档更新

### 2023-07-22

* 缠论计算：拆分三类买卖点情况，非为 9段内与 9段及以上 中枢的三类买卖点，可自行配置
* 配合 TV图表数据要求，修改各个交易所 日线及以上周期的返回时间
* 修改 新版 chanlun_chart WEB 项目相关bug


### 2023-07-17

      # 需要重新安装相关依赖包
      pip install -r requirements.txt

* 全新框架的 WEB 页面
* BUG 修复

### 2023-07-03

* 新增按照商品名称的拼音首字母进行搜索
* 文档搬家
* TradingViews 图表展示优化
* BUG 修复

### 2023-06-18

* 新增各类型买卖点是否计算的配置项
* 其他优化
* BUG 修复

### 2023-04-29

* 缠论计算，增加分型检查的K线范围设置
* 增加通达信美股的数据接口文件 （exchange_tdx_us.py）
* 文档更新

### 2023-04-17

* 缠论计算，增加分型不重叠的选项
* 修复通达信期货夜盘时间问题
* 其他bug修复

### 2023-03-27

> 包变更
>
> pip install alpaca-py ib_insync
>
> pip install -U polygon-api-client
>
> config.py 配置文件内容新增
>
>     # 盈透证券 TWS 设置
>     IB_HOST = '127.0.0.1'
>     IB_PORT = 7497
>     IB_CLIENT_ID = 1
>     IB_ACCOUNT = 'DU6941075'

* 新增 美股盈透证券 交易所接口，正常使用需要单独启动 （`script/crontab/script_ib_taksk.py`）脚本，用来转发 API 数据
* 新增同步美股数据脚本（`script/crontab/reboot_sync_us_klines.py`），数据来源：盈透证券
* 行情数据中，`date` 日期字段，统一增加时区信息（A股/港股/期货/数字货币时区： 'Asia/Shanghai' 美股时区：'US/Eastern'）
* 新增美股的周期转换方法 `convert_us_kline_frequency`，数据基于 盈透证券 的数据
* 新增策略 DEMO `StrategyZSTupo` (`chanlun/strategy/strategy_zs_tupo.py`) ，做中枢突破
* 其他 `BUG` 修复

### 2023-03-09

* 缠论计算更新
    * 新增笔内K线重叠拆分的配置，具体请参看 [缠论配置说明](缠论配置项说明.md)
    * 线段拆分逻辑优化
    * 分型包含是否成笔配置，只在 13 跟K线内部进行判断，多余 13 跟K线，则不进行包含判断
    * 其他BUG修复
* 新增 通达信期货交易所 (`tdx_futures`)，接口行情数据在盘后更新，盘中无实时行情
* 新增 通达信港股交易所 (`tdx_hk`)，接口行情有 15 分钟延迟
* 优化 `MySQL` 批量插入行情数据
* `Exchange` 接口增加 `default_code` / `support_frequencys` 两个方法，返回默认的代码和支持的行情周期

### 2023-02-24

* 缠论计算更新
    * 新增分型区域设置，可设置分型的区间计算的区域（三根或中间一根）
    * 走势段计算中枢类型，沿用线段的设置
    * 新增K线类型为 “缠论K线”，图表可展示合并处理后的缠论K线（MACD等指标计算使用合并后的缠论K线计算）
    * 计算 “方向中枢” 代码重写
    * 其他 Bug 修复
* 将 `config.py` 中关于缠论的设置，移动到 WEB 端进行可视化设置 （可以将 `config.py` 中的缠论设置删掉了，不再起作用）
* 回测：支持多进程回测（`run_process` 方法），只支持 信号回测模式
* TradingView 图表页，可展示自选涨跌，可调整自选分组
* 其他 Bug 修复 与 其他优化

### 2023-02-01

> 包升级
>
> pip install -U numpy pandas pyecharts
>
> pip install ccxt==2.7.12
>

* `install_windows.bat` 安装脚本，将 `python` 版本修改为 3.10
* 升级 `pyecharts` 、 `ccxt` 包为最新版本

### 2023-01-13

> 新增配置项 config.py
>
>     # 段内中枢超过几段进行拆分（单数，最小 9，包括中枢连接段）
>     xd_zs_max_lines_split = 11

* 缠论计算更新
    * 线段内部笔中枢扩展，进行线段拆分的自定义配置项
* 天勤期货行情数据(exchange_tq.py) 获取方式再优化
* 其他 bug 修复

### 2023-01-03

> 需要安装新增的python包
>
> pip install qiniu akshare snapshot_selenium
>

* 缠论计算更新
    * 线段拆分优化
    * 段内中枢bug修复
* 沪深A股行业概念板块信息接口替换，修改为 同花顺 接口（需要手动更新）[文档](FAQ.md)
* 任务监控，消息推送结构，可支持生成行情图片快照，需要按照文档配置后方可 [文档](消息推送支持图片.md)
* 自选列表，增加显示当日涨跌比例的显示（沪深A股建议用 富途牛牛 的接口，速度很快，否则会比较慢）
* 消息推送，如果是沪深A股，则会增加股票的 行业、概念 信息
* 天勤期货行情数据（kline、tick）获取方式优化（Beta）

### 2022-12-12

* 缠论计算
    * 线段拆分逻辑优化
    * 其他BUG处理与优化
* `web_batch_get_cl_datas` 异常处理优化
* WEB UI 布局优化调整
* 其他 BUG 修改

> `config.py` 添加配置，具体请参看 `configy.py.demo`

    # 特殊情况，拆分线段时，是否允许单笔成段    
    allow_split_one_line_to_xd = True    
    
    # 笔分型是否严格处理    
    # False : 不严格处理，允许顶的最低点低于底分型最低点，允许底分型的最高点高于顶分型的最高点    
    # True：严格处理，不允许顶的最低点低于底分型最低点，不允许底分型的最高点高于顶分型的最高点    
    allow_bi_fx_strict = True    

### 2022-12-02

* 缠论计算 Bug 修复
* 批量计算缠论数据方法 `batch_cls` 修改为 `web_batch_get_cl_datas`，其中的缓存方式，由内存修改为硬盘，减少内存的占用
* 通达信历史行情进行文件缓存，减少后续多次重复请求的时间

### 2022-11-26

* 缠论计算 Bug 修复
* 增加 `notebook` （图表（递归）_缠论图表.ipynb）
* 回测行情图表 `show_charts` 方法增加 `to_frequency` 参数，可低转高展示图表
* 沪深A行情数据转换 Bug 修复
* Web 行情图表，支持高级别调用低级别数据计算并展示，需要添加 `config.py` 配置，默认关闭
* 沪深A，判断是否交易时间方法更改，不再调用 Futu接口，直接写固定规则 周一-周五 9:30-11:30,13:00-15:00

### 2022-11-16

* 缠论计算 Bug 修改
* 回测方法中增加时间统计的代码
* 期货、数字货币增加 3m、2m 周期
* Demo Web 增加 TV 图表

### 2022-11-11

* 缠论计算
    * 增加 趋势段 的计算，根据走势段递归而来
    * 增加新的中枢画法：分类中枢
    * 优化类二类、类三类买卖点规则
    * 新增二类买卖点的规则
    * Bug 修复
* 图表展示
    * 新增更多的图表展示配置
    * 支持将小周期数据转换成高周期数据并进行展示
    * 新增 Trading View 图表展示（测试版本，会有些问题，后续优化）
* 其他

### 2022-10-28

* 缠论计算，线段划分添加新的规则
* Bub 修复

### 2022-10-14

* 缠论计算
    * 笔标准化逻辑修改
    * 笔对象 `BI` 中的 `td` 属性去除，使用 `cl_utils.py` 中的 `bi_td()` 方法进行判断
    * 特殊线段的处理（中枢九段、段内不同向中枢）
    * 删除线段、走势段标准化的配置
    * 买卖点的重新梳理 [详情](缠论买卖点和背驰规则.md)
    * 可自定义实现自己的买卖点规则，参考 `cl_interface.py` 中的 `user_custom_mmd()` 方法
    * 中枢计算规则修改，修复个别情况下中枢范围计算错误

* 项目默认 `Python` 版本修改为 `3.10`，目前项目支持版本为 `3.7/3.8/3.9/3.10`
* 掘金下载A股数据，K线时间修改为后对其时间（对于已经下过过的数据，建议删除重新下载）
* 回测 `Strategy` 策略基类增加 `on_bt_loop_start` 方法
    * 回测专用，每次回测循环都会调用该方法，可以执行下自己的特定逻辑
    * 例如判断当前的大盘环境，是否可进行交易；初步筛选可交易的品种，在 `open` 进行判断品种是否可交易，大大加速回测速度
* `exchange.py` 中K**线合并的方法重写**，对于期货 10:15 的出来，掘金和天勤是不同的逻辑，可自行选择（通过打开关闭注释实现）
* `kcharts.py` 画图修改
    * 修复在同一分型，笔/线段/走势段 同时出现同一类买卖点或背驰，只显示笔买卖点或背驰的 bug
    * 图表买卖点展示修改，修改为 1B/2B/L2B/3B/L3B/1S/2S/L2S/3S/L3S，减少图表占用面积，显得比较简洁
* 其他 `BUG` 修复

### 2022-09-30

* 缠论计算
    * 新增 平均K线 支持，可以使用 平均K线 数据，计算缠论数据
    * 线段的继续优化（已完成线段的延续，特殊情况线段破坏，未完成线段处理，线段标准化处理）
    * 新增 线形态分析（`chanlun\cl_analyse.py (LinesFormAnalyse)`，可在图表中进行展示，待完善
    * 将力度比较的方法提出来，可自行修改线的力度并进行比较，来判断是否背驰（`cl_interface.py 文件 compare_ld_beichi 方法`）
    * 修改默认的缠论配置值
* 回测更新
    * 触发止损后的执行价格，修改为当前最新价格
    * 新增 atr 移动止损的方法
* 画图更新
    * 增加是否显示 线形态分析
    * 增加是否显示 顶分型提示
    * 增加是否在 MACD 幅图显示线的力度，可指定显示笔或线段的力度
* 通达信行情数据（`exchange_tdx.py`），K线数量由2400增加到4000
* 新增 下载A股（掘金）数据脚本 `script\crontab\reboot_sync_gm_a_klines.py`
* 将 掘金配置 放在 config.py 中 （包括 掘金服务IP地址、Token 信息）
* `行情回放练习` 功能修复，现在可以正常使用了，需要提前下载行情数据

### 2022-09-02

* 缠论计算，优化线段划分
    * 特征序列有缺口，查找后续反向分型时，如创出新高或新低，原线段将延续
    * 最后线段如果未完成，结束分型画在最高或最低处

### 2022-08-29

* 缠论计算更新
    * 线段划分重新梳理，建议更新（kcharts.py 中，可以去除画线段特征序列的注释，可在图表中展示线段的顶底特征序列分型，直观了解之前线段的生成逻辑）
    * 增加起始计算的时间参数，如指定起始时间，则从设置的时间开始计算分型/笔/线段等数据
    * cl_interface.py 中 CL_BI_FX_STRICT 默认为 True （笔分型严格处理）
    * 线的角度方法 LINE.jiaodu() 修改，固定横坐标长度，利于不同价格间的相对比较（不一定正确）
* 策略回测更新
    * 策略中的 open 方法，增加 poss 参数（当前标的的持仓信息）
    * 策略中的 close 方法，返回值类型增加 List[Operation]]，可返回多个操作指令
    * 回测中，信号模式下，也会根据手续费率，统计手续费情况，最终的盈亏会扣除手续费
    * 回测中，触发止损后，止损价格由原来的最新价格，修改为设置的止损价
    * Operation 策略指令对象中，增加 pos_rate，key 参数，可指定开仓 or 平仓的比例，通过 key 值可避免多次重复执行
    * Strategy 策略类中增加更多的指标计算方法
    * 新增 StrategyFuturesXDZS() 策略，期货基于线段的中枢震荡策略，[详情](基于线段的中枢震荡策略.md)
* 数字货币 exchange_binance.py 返回更多K线数量（最大10000，需要数据库中有足够的数据，建议每天执行同步行情脚本）、
* kcharts.py 画图，去除力度小于 5 的分型展示，减少画图数据，减少数据传输数量，提高些许图标响应速度（也许吧）
* kcharts.py 画图，多中枢下，一笔/段 中，同类型的买卖点背驰，只显示一个，避免重复信息过多
* 增加 期货、数字货币 10分钟周期
* 其他 BUG 修复

### 2022-07-29

*

新增：通过掘金量化，获取期货主连合约数据脚本，并同步到数据库中，进行回测使用 `script/crontab/reboot_sync_gm_futures_klines.py`

* 策略 `Operation` 操作对象，增加 `opt : lock` 锁仓的操作，应用于期货策略
* 缠论配置项：修改为保存到 `Redis` 中，并且可以单个品种独立设置，相关方法在 `src/chanlun/cl_utils.py` 文件中
* WEB 页面，可设置更多的图表参数（新增副图、成交量均线、RSI、ATR、CCI、KDJ）
* WEB 页面，缠论配置可设置多个中枢类型，并在图表上进行展示
* WEB 页面，可设置图表初始化展示的K线数量（如果觉得 1000 太多，图太小，可自行改小一些）
* WEB 页面，新增 `趋势通道线`，根据自行设置的参数，根据最后 N 个完成的 笔 or 线段，高次高连线、低次低连线，作为趋势通道线进行参考
    * 设置值：xd,5 (根据最后5个已完成线段画趋势通道线)；bi,11（根据最后11个已完成的笔画趋势通道线）
    * ![趋势通道线示例](img/update_qstd_line.png ':size=400')
* WEB 任务配置，删除缠论配置设置，修改为：读取 WEB 设置的配置，进行计算并通知，避免两边配置不同，看不到提醒的背驰或买卖点
* WEB 数字货币持仓列表，增加一键平仓按钮
* 其他相关优化与BGU修复

### 2022-07-11

* 策略回测，在K线回放类中，增加 `load_data_to_cache`；
    * 表示是否将数据装在进内存，默认 True，如果内存告急，可将其设置为 False，以时间换空间，会比原来回测时间多一倍
* 策略参数优化，同样增加 `load_data_to_cache` 参数，用来减少内存使用；
    * 参数优化会创建多个进程跑策略，如果都将数据加载如内存，会占用太多内存，内存小会跑失败，可在参数优化中将其设置为 False
    * `res = BT.run_optimization(setting, max_workers=None, next_frequency='d', evaluate='profit_rate', load_data_to_cache=False)`
* 策略基类中 `Strategy`，增加 `judge_macd_back_zero` 方法，判断中枢是否有回拉零轴
* 增加 `KlinesGenerator` K线生成（分钟），目前只支持分钟级别的生成，其他小时、日线需要判断不同市场的交易时间，比较麻烦，不做呢
    * 示例参考：[合成自定义K线数据（分钟）](合成自定义K线数据（分钟）.md)
* 缠论计算，可同时计算多个中枢及相对应的买卖点背驰信息
    * 示例参考：[多中枢类型相同买卖点策略](多中枢类型相同买卖点策略.md)
* `cl_utils.py` 增加获取笔内缺口数量的方法 `bi_qk_num(cd: ICL, bi: BI)`
* 页面操作，增加图表订单管理，可在图表中增加指定的订单信息，并统一了下订单保存和读取的方法
* 增加选股方法示例：
    * `xg_multiple_zs_tupo_low_3buy` : 高级别中枢突破，在低级别有三买
    * `xg_single_pre_bi_tk_and_3buy` : 在三买点前一笔，有跳空缺口
* 沪深行情页面，增加 F10资料 快捷入口，可直达 东方财富的F10 页面
* 自选组，沪深的参数由原来的 `stock` 更改为 `a`
* 文档地址修改为：https://chanlun-pro.readthedocs.io/

### 2022-06-24

* 回测的 `signal` 模式，图表中的累计平仓盈亏曲线改为资金曲线，按照时间累加展示 平仓盈亏+持仓盈亏，更好展示策略资金变化情况；
* 行情图表，交易量副图增加交易量均线，默认是 5、60两条均线；
* 增加了一些选股方法；
* 修复 MACD 指标计算偏差 BUG
* 修复其他BUG

### 2022-06-17

* 运行策略缠论参数优化方法，增加 `next_frequency`、`evaluate` 参数，可设置策略运行循环的周期，结果评估的指标；
* `BackTest` 类 `show_charts` 展示图标方法，增加 `chart_config` 参数，可设置展示图表配置；
* 回测配置 `cl_config`，可按照策略执行标的，分别设置对应的缠论配置项，例如：'cl_config': {'BTC/USDT': {...}, 'ETH/USDT':
  {...}}
* 获取行情接口增加重试机制，需要安装 `tenacity` 依赖包；
* TDX行情第一次连接会选择最优ip服务器，并保存到 redis 中；
* 参考 mootdx 项目，给 tdx 行情数据默认做前复权处理；
* 图表均线可设置多个（最多5个），使用英文逗号（,）分割，例如:5,10,60

> 需要执行 pip install tenacity 安装依赖包

### 2022-06-08

* 缠论计算修改
    * 将 MA、BOLL 指标移除，放在 `kcharts.py` 进行计算
    * 去除非必要的计算，改为方法，在使用时在计算，大约节省 30% 时间
    * 方向中枢：严格处理，进入段要是中枢最高或最低才可以
    * 去除 ZS 对象的 ld （力度）属性
    * 将 zslx_*** 配置，修改为 zsd_***
    * 修复其他 bug
* notebook 增加 `数据回放测试.ipynb`，可以配合策略回测，检查动态的缠论计算过程
* `backtest.py`，回测结果的 table，增加 汇总 的结果展示
* 策略回测增加进度条，展示当前回测进度
* `exchange_tdx.py` 请求行情的 klines 增加缓存，避免每次都全量多次查询行情数据
* 自选类增加清空方法 `clear_zx_stocks`
* 项目文档重新整理，在线地址 https://chanlun-pro.readthedocs.io/
* 策略
    * 增加高级别根据低级别1类买卖点信号开仓策略，采用多周期的笔进行判断（`strategy_son_level_1mmd.py`）
    * 增加高级别根据低级别1类买卖点信号开仓策略，采用低级别递归进行判断（`strategy_zsd_xd_bi_1mmd.py`）
* 选股策略
    * 新增：`xg_single_day_bc_and_up_jincha()` （日线级别，倒数第二个向下笔背驰，等待后续macd在水上金叉）

> 策略是否有效，和 `cl_config` 配置也有很大关系，不同的市场适用不同的缠论配置，可根据 `OptimizationSetting` 进行参数优化，查找最优配置
>
> `chanlun.backtesting.backtest.BackTest:246` 节省参数优化执行的时间，这里可以手动设置每次循环的周期
>
> `chanlun.backtesting.backtest.BackTest:257` 这里设置参数优化评估的结果值，可以设置为 max_profit_rate ,查找最大盈亏百分比总和最大的

### 2022-05-27

* 缠论计算修改
    * 增加分型包含配置：前分型包含后分型、后分型包含前分形（类似顶底包含配置）
    * 修复bug
* 批量计算多周期方法 batch_cls 转移到 cl_utils.py 文件中，并增加缓存
* WEB图表中计算缠论增加缓存，加速行情二次加载速度

### 2022-05-20

* 缠论计算修改
    * 增加笔分型成笔条件（是否允许 顶的最低点低于底分型最低点，底分型的最高点高于顶分型的最高点）
    * 增加获取 最后笔、线段中枢的 方法（get_last_bi_zs、get_last_xd_zs）
    * 增加中枢类型：方向性中枢

> 备注：
>
> 新增的缠论配置放在 cl_interface.py 文件中，不可在 web 页面中进行变更，默认为 False，与原来计算方式保持一致；
>
> 获取最后中枢是从最后一笔倒推的中枢，和原中枢计算的最后一个中枢会有差异；
>
> 方向性中枢：计算的中枢，进入与离开的方向一致（除最后一个未完成中枢）

* 支持掘金量化回测，并增加示例 [run.py](src/cl_myquant/run.py)
* 增加基于最后一个中枢的策略示例 [strategy_last_zs_3mmd.py](src/chanlun/strategy/strategy_last_zs_3mmd.py)

### 2022-05-13

* 缠论计算修改
    * 修改默认配置，分型包含为允许、笔中枢类型为标准、中枢位置关系为 zggdd
    * 类3买点逻辑优化
    * 多级别分析的类转移到 chanlun.cl_analyse.py 文件中
    * 修复计算bug
* 回测增加缠论参数优化功能，参看 [回测_缠论参数优化](notebook/回测_缠论参数优化.ipynb)
* online_market_datas.py 获取线上行情数据增加缓存，避免多次重复请求，需要手动调用 clear_cache 清除缓存
* 修复 行情回放练习 的bug

### 2022-05-06

* 缠论计算修改
    * 分型包含是否成笔处理逻辑bug修复
    * 二类买卖点，增加出中枢后不创新高/新低的买卖点提示
    * 修改分型强度计算方式
    * 增加走势段中枢，以及走势段买卖点
    * 三类买卖点的中枢判断，去除级别的限制

* 回测框架修改
    * 增加回测模式，分为：信号、交易、实盘 三类
    * 修改回测行情数据获取方式，通过基准代码，获取循环的时间列表，以此循环执行标的回测
    * **修改策略接收的缠论数据对象，CLDatas 变更为 MarketDatas，可获取除当前标的以外的数据，如 大盘指数 等**

* 策略新增与修改
    * 增加关于A股市场的交易策略 strategy_a_single_all_mmd.py，单周期，个人认为效果不理想，可以用来参考学习
    * 策略结果查看 [回测_沪深股票策略.ipynb](notebook/回测_沪深股票策略.ipynb)

* 行情图表在 Jupyterlab 环境可通过参数修改副图，来显示其他技术指标（暂不支持web）
* 修改行情图表显示订单记录的逻辑，不需要额外的时间转换
* 行情图表展示优化， 买卖点直接显示文字，更加直观；中枢颜色统一，笔中枢为白色，线段中枢为黄色，不在区分方向，之前的太花了
* 行情图表增加强分型提示
* 实盘交易示例修改，以适应新的回测运行方法
* VNPY 回测策略简化，更加方便对接项目中的策略并执行
* 增加从聚宽平台导出数据，之后在导入到本地数据库中，用于回测
* 其他bug修复

### 2022-04-29

**需要修改配置文件，参考 config.py.demo 进行更改**

**需要修改配置文件，参考 config.py.demo 进行更改**

**需要修改配置文件，参考 config.py.demo 进行更改**

```
    # 需要安装的包
    pip install alpaca-trade-api
    pip install polygon-api-client
    pip install MyTT
```

* 增加美股行情支持 @Jiang Haoquan 提供
* 交易所对象整理，所有交易所对象放在 exchange 包中，可在 config.py 中配置 web 所使用的各个市场交易所
* 增加更多选股条件设置，支持多周期选股，在 src/chanlun/xuangu/xuangu.py
* 回测图表优化
* 策略类 Strategy 增加一些策略中常用的方法（最后完成笔、强停顿、验证分型等等）
* 增加binance交易所获取K线数量，原 1000 到 1500 （数据库支持可到 2000）
* 重写多级别分解，可根据高级别笔、段，查找所包含的笔、段，并重新计算中枢，判断其中是否有背驰信息，参看 cl_interface.py
* 简单优化了下背驰策略
* 项目自带回测相关 bug 修复
* 代码优化 @Tim Lee 提供
    * 删除对keys()的不必要调用
    * 使用if表达式替换if语句
    * 使用items()直接解包字典值
    * 将重复代码提取到方法中
    * 调用itertools.product替换嵌套的for循环
    * 简化生成器表达式，用list extend替换 for append 循环
    * 用f-string替换interpolated string进行格式化
    * 使用next函数代替for循环
    * 简化序列长度比较
    * 将for循环转换为列表推导
    * 使用contextlib的suppress方法来消除错误
    * 删除保护条件后不必要的else
    * 合并嵌套if条件，将同一变量的多次比较替换为in运算符
    * 用 None 替换可变的默认参数
    * 使用any()代替for循环
    * 使用命名表达式来简化赋值和条件
    * 精简和重构部分代码

* 缠论计算修改
    * 个别配置下，线段计算错误
    * 中枢对象增加 macd 上穿下穿零轴，金叉死叉信息
    * 中枢振幅算法修改，改为中枢重叠区占整个中枢的百分比
    * 初始线段算法修改
    * 修复中枢位置计算bug，影响一二类买卖点

### 2022-04-16

* 完善相关安装文档（Windows、Ubuntu），简化Windows安装步骤
* 沪深行情获取不在使用富途（tick、板块信息和交易时间 数据还是需要富途才可正常获取）
* 沪深行情页面去掉根据时间获取的功能
* WEB图表增加简单画图功能，成交量与光标展示优化（感谢 @阿仔哥 提交的代码）
* **回测代码整理，相关文档 docs/缠论回测与交易指南.md**
* **实盘交易脚本整理，包括 沪深、港股、数字货币、期货市场；参看 docs/缠论回测与交易指南.md**
* **增加VNPY回测与实盘交易支持，文档参看 docs/vnpy使用指南.md**

### 2022-04-05

### chanlun-pro 项目更新

* 缠论核心 cl.py 代码加密并增加授权验证
* 增加本地选股脚本 script/xuangu.py，用于代替之前聚宽平台的选股功能
* 统一将页面缠论配置项收入到伸缩栏进行设置（页面中的两个图表使用同一套缠论配置）
* 缠论计算增加N项配置，详情参考页面设置

> cl.py 加密并打包，需要使用授权 licenses 文件才可使用；    
> 在 /src/pytransform 目录有一个试用 licenses 文件，将其复制并重命名为 license.lic 即可使用，有效期到 2022-04-12；    
> 请各位 VIP 将自己需要绑定的 mac 地址单独发我，给予生成授权文件；
> Windows 用户执行 getmac 命令获取；Linux、MacOS 执行 ifconfig 命令获取；
>
> 增加了多个缠论配置项，任务配置需要重新设置并保存才可生效

### 2022-03-25

### chanlun-pro 项目更新

* 缠论中枢增加 段内中枢 功能，在线段内查找并标识笔中枢
* 增加中枢区间配置，可设置 实际高低 与 顶底端点 两个配置，用来计算 中枢高低点
* 增加趋势线，按照线段的特征序列计算得来的趋势线
* LINE (BI/XD) 对象的 high、low 修改为实际的高低点，增加 ding_high() di_low() 方法获取端点的高低点
* 去除了线段是否完成的配置
* 画图优化，深色爱护眼睛模式，未完成笔、线段、趋势，使用虚线标识
* 优化指标计算，根据设置的最大值，来获取计算的价格序列，均线参数等可设置大于100的值
* 修复 bi.done 不更新的 bug
* 修复 中枢 zg、zd 计算错误 bug
* 回测的 notebook 实例优化，简化了代码，可直接调取封装的方法，参考 回测_数字货币策略.ipynb
* 修改了 Strategy 策略的两个方法名，修改为 open、close 更好理解其功能
* 增加港股的任务配置
* 简单完善了写策略编写文档：BACK_TEST.md

### chanlun 同步更新以上 缠论计算 功能

### 2022-03-22

### chanlun-pro 项目更新

* 缠论线段计算 bug 修复
* 将港股与沪深股市分开两个页面展示
* 图表高度在（沪深、港股、期货）可单独设置大图或小图

> 需要在 config.py 中增加 香港股票自选分组 配置

*chanlun 项目统一周五更新*

## 2022-03-20

### chanlun-pro 项目更新

* 股票列表通过 通达信 获取
* 增加股票行情获取条数，原来 800 条增加到现在的 2400 条

> 需要重新安装 pytdx 包   
> pip3 uninstall pytdx   
> pip3 install wheel   
> pip3 install package/pytdx-1.72r2-py3-none-any.whl

## 2022-03-18

### chanlun 项目更新

* 增加线段中枢以及线段买卖点
* 画图展示优化
* 增加多个参数（缠论、画图），可按需自定使用

具体可参考：https://github.com/yijixiuxin/chanlun/tree/main/example

### chanlun-pro 项目更新

* 图表增加均线
* 增加页面可定义指标参数设置
* 增加画图自定义展示开关
* 任务配置监控，增加线段的背驰与买卖点监控
