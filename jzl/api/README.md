# 竞争力API使用规范v1.0

目前公开了用于查询的两个api，访问类型支持：

- http
- https

> 建议使用https，以获得安全性保障，基于https的api，可兼容ios、微信小程序的平滑演进

## API- select

该api用于选择全网城市汇总数据

### 基本路径

```html
https://api.imaoda.com/jzl/select
```

### 请求参数说明

参数|格式|说明
---|---|---
month|201702|必选
city|Beijing 或 10100|可选，默认返回所有城市
type|json 或 csv|默认json

### 返回数据格式

#### json数据

```js
'2017-01':{
    {lt:{...},yd:{...},dx:{ //总汇总
        g4:[0总点,1总用户，2覆盖，3质量，4速度in，5速度out，6时延，
            [0-163,1-baidu,2sina,3taobao,4qq,5youku,6iqiyi,7sohutv,8qqtv,9baiduv,10letv,11tudou],
            8覆盖率,9占网比 //8、9仅4G有
        ],
        g3:[...], //3G指标，同4G
        g2:[...], //2G指标，同4G
    }
}
```

#### csv数据

> 注：导出csv数据请手动修改后缀为.csv后打开

字段名称|字段释义
---|---
city|城市
month|月份
vendor|运营商
net|制式
total_points|总采样点
total_users|总用户数
coverage|覆盖良好比例
quality|质量良好比例(2G/3G无效)
speedin|下载速率
speedout|上传速率
p_163|ping时延
p_baidu|ping时延
p_sina|ping时延
p_taobao|ping时延
p_qq|ping时延
p_youku|ping时延
p_iqiyi|ping时延
p_sohutv|ping时延
p_qqtv|ping时延
p_baidutv|ping时延
p_letv|ping时延
p_tudou|ping时延
lte_percent|4G占网比
vendor_market|覆盖率



### 一般实践

#### a) 查看北京在1月的数据

https://api.imaoda.com/jzl/select?month=201701&city=Beijing

#### b) csv导出所有城市1月的数据

https://api.imaoda.com/jzl/select?month=201701&type=csv

## API- selectscene

该api用于选择按照场景汇总的数据

### 基本路径

```html
https://api.imaoda.com/jzl/selectscene
```

### 请求参数说明

参数|格式|说明
---|---|---
month|201702|必选
city|Beijing 或 10100|可选，默认返回所有城市
type|json 或 csv|默认json

### 返回数据格式

#### json数据

```js
'2017-01':{
    {lt:{...},yd:{...},dx:{ //总汇总
        g4:[0总点,1总用户，2覆盖，3质量，4速度in，5速度out，
            6网页时延，7视频时延，
        ],
        g3:[...], //3G指标，同4G
        g2:[...], //2G指标，同4G
    }
}
```

#### csv数据

> 注：导出csv数据请手动修改后缀为.csv后打开

字段名称|字段释义
---|---
city|城市
month|月份
vendor|运营商
net|制式
scene_id|场景id
total_points|总采样点
total_users|总用户数
coverage|覆盖良好比例
quality|质量良好比例(2G/3G无效)
speedin|下载速率
speedout|上传速率
p_html|网页时延（6项平均）
p_video|视频时延（6项平均）

```js
//scene_id 场景id的对应关系

$changjing=array( 

		"市区"=>1,
		"县城"=>2,
		"行政村"=>3,
		"A类乡镇"=>4,
		"B类乡镇"=>5,
		"C类乡镇"=>6,
		"一类校园"=>7,
		"二类校园"=>8,        
		"三类校园"=>9,
		"5A级景区"=>10,
		"4A级景区"=>11,        
		"3A级景区"=>12,
		"3A级以下景区"=>13,        
		"国道"=>14,
		"机场高速"=>15,
		"跨省高速"=>16,
		"跨省高铁"=>17,
		"省内高铁"=>18,
		"动车线"=>19,        
		"普通铁路"=>20,
		"省道"=>21,
		"省内高速"=>22,
		"水运航道"=>23
);

```


### 一般实践

#### a) 查看北京在1月的数据

https://api.imaoda.com/jzl/selectscene?month=201701&city=Beijing

#### b) csv导出所有城市1月的数据

https://api.imaoda.com/jzl/selectscene?month=201701&type=csv


## API- selectprovince

该api用于选择全网按省汇总数据

### 基本路径

```html
https://api.imaoda.com/jzl/selectprovince
```

### 请求参数说明

参数|格式|说明
---|---|---
month|201702|必选
province|Beijing 或 101|可选，默认返回所有城市
type|json 或 csv|默认json

### 返回数据格式

#### json数据

```js
'2017-01':{
    {lt:{...},yd:{...},dx:{ //总汇总
        g4:[0总点,1总用户，2覆盖，3质量，4速度in，5速度out，6时延，
            [0-163,1-baidu,2sina,3taobao,4qq,5youku,6iqiyi,7sohutv,8qqtv,9baiduv,10letv,11tudou],
            8覆盖率,9占网比 //8、9仅4G有
        ],
        g3:[...], //3G指标，同4G
        g2:[...], //2G指标，同4G
    }
}
```

#### csv数据

> 注：导出csv数据请手动修改后缀为.csv后打开

字段名称|字段释义
---|---
province|省份
month|月份
vendor|运营商
net|制式
total_points|总采样点
total_users|总用户数
coverage|覆盖良好比例
quality|质量良好比例(2G/3G无效)
speedin|下载速率
speedout|上传速率
p_163|ping时延
p_baidu|ping时延
p_sina|ping时延
p_taobao|ping时延
p_qq|ping时延
p_youku|ping时延
p_iqiyi|ping时延
p_sohutv|ping时延
p_qqtv|ping时延
p_baidutv|ping时延
p_letv|ping时延
p_tudou|ping时延
lte_percent|4G占网比
vendor_market|覆盖率



### 一般实践

#### a) 查看湖北在1月的数据

https://api.imaoda.com/jzl/selectprovince?month=201701&province=Hubei

#### b) csv导出所有省份1月的数据

https://api.imaoda.com/jzl/selectprovince?month=201701&type=csv
