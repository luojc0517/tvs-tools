[TOC]

### 领域名称

历史服务

### 意图列表

| Intent        | Description  |
| ------------- | ------------ |
| search_today  | 历史上的今天 |
| search_person | 历史人物     |

### 数据示例

##### search_person无模版

```json
/*
 * search_person 纯文本模版
 * 语料：历史人物
 * BOT：410音响 (c76f35f0-37f3-4f91-bf40-2bce9211e9b5)
*/ 
// ======================= Json数据 =======================
{
    "controlInfo": {
        "audioConsole": "", 
        "textSpeak": "true", 
        "type": "TEXT", 
        "version": "1.0.0"
    }, 
    "listItems": [
        {
            "textContent": "唐太宗的名字是: 李世民。"
        }
    ]
}
```

#####search_today纯文本模版

```json
/*
 * search_today 纯文本模版
 * 语料：历史上的今天
 * BOT：410音响 (c76f35f0-37f3-4f91-bf40-2bce9211e9b5)
*/ 
// ======================= Json 数据 =======================
{
	"controlInfo": {
		"audioConsole": "", 
        "textSpeak": "true", 
        "type": "TEXT", 
        "version": "1.0.0"
	},
	"listItems": [{
		"textContent": "1918年 德军使用贝尔塔巨炮轰击巴黎
1923年 紫禁城发生大火
1930年 埃及六月起义爆发
1931年 东北发生中村事件
1933年 当代指挥大师阿巴多生日
1945年 联合国托管理事会成立
1946年 《美国军事援华法案》通过
1946年 国民党军进攻中原解放区
1946年 解放战争开始
1946年 刘善本驾机起义
1950年 南非自由日
1954年 尼赫鲁评价“五项原则”
1965年 “六·二六”指示
1975年 印度反对派指控英·甘地在选举中舞弊
1988年 “国际禁毒日”定名
1993年 我国首次在国内发行外币债券
1994年 “引大入秦”总干渠贯通
1997年 中韩漂流队失踪13天虚惊一场
2000年 人类基因组工作草图亮相",
	}]
}
```

