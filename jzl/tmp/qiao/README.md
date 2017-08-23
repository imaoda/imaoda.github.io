# 校园场景处理规范 V1

## 文件初步处理

### 1 文件格式转换

目前，各个地市上报的文件是 mapinfo格式的，需要做一些格式转换，才能给程序使用。

- 使用mapinfo软件 或者 [tab2mif](http://pan.baidu.com/s/1kVSJk5x)软件进行转换，得到一对mif mid 文件

> 注：mid文件是网格中文名，mif文件是网格的边缘点数组，用文本打开可看到文件详情


### 2 统一命名

> [附件：城市id.xlsx](http://pan.baidu.com/s/1jIKJIa6)

- 以csv方式打开mid文件
- mid文件中保留【索引】和【微网格名称】，通过:符号进行字符串链接，如：1010000001:北京大学
- 注意：切记不要打乱序列顺序，引号用半角


```
1010000001:南京西路路口南
1010000002:新街口人才大厦
1010000003:光华大道西路科技园
1010000004:云南印象村
```
【索引】为： 城市id*10000+行号；关于城市拼音和城市id，可参考，部分城市需注意

- 宿州市	Suzhou1
- 玉林市	Yulin1
- 伊春市	Yichun1
- 泰州市	Taizhou1
- 抚州市	Fuzhou1

### 3 文件编码转换

mid文件需要进行utf-8编码转换

1. 用notepad或ultraEdit等工具打开xx.mid
2. ctrl+A ctrl+C 复制全部mid文件内容到[vs-code](https://code.visualstudio.com/Download)中
3. 在vs-code中保存

### 4 文件存放路径规范

```
- China
    - Sichuan
        1.mid
        1.mif
    - Shandong
        Jinan
            1.mid
            1.mif
        Qingdao
            1.mid
            1.mif
        ...
    - Fujian
        1.mid
        1.mif
```

