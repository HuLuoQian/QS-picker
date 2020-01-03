## 可直接拖进项目运行

## QQ交流群: 750104037 [点我加入](https://jq.qq.com/?_wv=1027&k=5OyZoXa)

---
## 作者想说

如果该插件有什么问题还请大家说出来哦，还有如果有什么建议的话也可以提下呐 ~
如果觉得好用，可以回来给个五星好评么~~(❁´◡`❁)\*✲ﾟ\*  蟹蟹~拜托啦~

---
## 组件简介
提取了inputs组件的picker类型合集，参考了Color-Ui的模态框展示方式

### 该插件在支付宝小程序不能运行, 推荐使用[QS-inputs-split](https://ext.dcloud.net.cn/plugin?id=652)中的picker，兼容性更强，并且更好用

---
# 更新说明

| 版本号| 更新说明|
| --------- | :-------- |
| 1.7| 修改date默认格式为/ |
| 6.0| 修复date类型下设置dateFormatArray无效问题 |
| 5.0| 1、新增mode、zIndex、lineHeight、bgColor_title、autoHide、titleColor、contentColor等属性 详见1.<br />2、buttonSet中 新增 cancleColor、confirmColor等属性 详见1.0.2 |
| 4.0| 修复从后端获取数据拼接赋值后不能使用问题  |
| 3.0| 1、废弃show属性，展示方式请使用ref调用show方法<br />2、新增title属性，为picker的标题， title文字的大小为picker内的文字大小系数上加.002<br />3、优化button按钮的文字大小为picker内的文字大小系数上加.005<br />4、新增并更改@showQSPicker、@hideQSPicker为picker显示或隐藏时的回调  |
| 2.0| 1、新增showReset属性（每次显示是否重置）<br />2、修复date类型<br />3、完善文档  |

---

## 显示picker：this.$refs.自定义的ref名称.show();

## 隐藏picker：this.$refs.自定义的ref名称.hide();   (一般不用，选择后自动隐藏)


# 1. 传给QS-picker的属性

| 属性名| 是否必填| 值类型|  默认值| 说明|
| --------- | -------- | -----: | --: |
| ~~show（废弃, 请使用ref调用show方法）~~| 是| Boolean| `false`|   控制picker显示或隐藏 |
| type| | String |  |   picker的类型, 详见1.0.0 |
| dataSet| | Object|  | 各类型携带的数据, 详见1.0.1 |
| pickerId| | String|  |   自定义的picker标识 |
| height| | Number | `.3` | picker的高度, 设备的高度乘以此数值 |
| indicator_style| | String| `'height:' + (Sys.screenHeight*.09) + 'px;'` | picker的单行样式 |
| fontscale| | Number | `.02` | picker内的字体大小, 设备高度乘以此数值 |
| width| | Number | `.8` | picker的宽度, 设备宽度乘以此数值 |
| fontscale| | Number | `.02` | picker内的字体大小, 设备高度乘以此数值 |
| buttonSet| | Object|  | 按钮设置, 详见1.0.2 |
| @hideQSPicker| 是| Function|  | 取消或确定选择的隐藏picker回调 |
| @showQSPicker| 是| Function|  | 取消或确定选择的隐藏picker回调 |
| @confirm| 是| Function|  | 确定选择时的回调, 携带用户选择的数据并自动触发@hideQSPicker |
| showReset(2.0新增)| | Boolean|  | 每次显示时是否重置picker的value为初始化 |
| title(3.0新增)| | String|  | picker的标题 |
| `v5.0新增` |          |        |     |
| mode| | String| `middle` | 展示模式, 详见 1.0.3 |
| zIndex| | Number\|String| `9999` | z-index属性 |
| lineHeight| | Number| `.09` | picker内单行高度系数 |
| bgColor_title| | Color| `#F8F8F8` | title块背景颜色 |
| autoHide| | Boolean| `true` | 用户确定选择后是否自动隐藏 |
| titleColor| | Color| `#999` | title的文字颜色 |
| contentColor| | Color| `black` | picker-view内的文字颜色 |


## 1.0.0 type属性说明

| 值| 说明|
| --------- | -------- |
| date| 日期时间 |
| city| 省市区 |
| provincialStreet| 省市区乡镇街道|
| custom| 自定义|
| custom2| 自定义2， 比custom返回数据更简单|

## 1.0.1 dataSet属性说明

### 1.0.1.0.1 `date类型`

| 属性名| 是否必填| 值类型|  默认值| 说明|
| --------- | -------- | -----: | --: |
| startYear| | Number| `new Date().getFullYear() - 5` |   开始年数 |
| endYear| | Number| `new Date().getFullYear() + 5` |   结束年数 |
| defaultValue| | String| 此刻| 格式为`2019/05/27 10:54:00`、`2019/05/27`的初始日期 |
| dateMode| | Number |  `3`|   取值为1-6的值，依次从左向右为年、月、日、时、分、秒的列数 |
| dateFormatArray| | Array|  `['-', '-', ' ', ':', ':']`| 确认选择后返回的格式，依次是年、月、日、时、分、秒之间的分隔符 |

示例代码:

```javascript
{
  startYear: 2018,
  endYear: 2020,
  defaultValue: "2019/05/27 10:54:00",
  dateMode: 3,
  dateFormatArray: ['-', '-', ' ', ':', ':']
}
```

### 1.0.1.0.2 `city类型`

| 属性名| 是否必填| 值类型|  默认值| 说明|
| --------- | -------- | -----: | --: |
| defaultValue| | Array| `[0,0,0]`| 初始值 |

示例代码:

```javascript
{
 defaultValue: [0,0,0]
}
```

### 1.0.1.0.3 `provincialStreet类型`

| 属性名| 是否必填| 值类型|  默认值| 说明|
| --------- | -------- | -----: | --: |
| defaultValue| | Array| `[0,0,0,0]`| 初始值 |

示例代码:

```javascript
{
 defaultValue: [0,0,0,0]
}
```

### 1.0.1.0.4 `custom类型`

| 属性名| 是否必填| 值类型|  默认值| 说明|
| --------- | -------- | -----: | --: |
| itemArray| 是| Array| | 需循环展示的数据 |
| defaultValue| | Array| | 初始值 |
|linkage| | Boolean| `false`| 是否联动|
|linkageNum| | Number| | 联动级数|
|steps| | Object| | 自定义阶级变量名，详见下方示例与说明|

### 1.0.1.0.4.0.1 custom的steps属性说明
| 属性名| 是否必填| 值类型| 默认值| 说明|
|------|----|----|----|-------|
| step_1_value| | String| | 一级显示属性名|
| step_2_value| |String| |二级显示属性名|
|step_2_item| | String| | 二级联动数组属性名|
|step_3_value| | String| | 三级显示属性名|
|step_3_item| | String| | 三级联动数组属性名|
注：详见下方示例

示例代码:

```javascript
{
  itemArray: [{
  value_1: "江西", //value_1变量名需与下方steps.steps_1_value相同
  /*
  可添加多项自定义想要的数据
  */
  item_2: [{ //item_2变量名需与下方steps.steps_2_item相同
  	value_2: "南昌", //value_2变量名需与下方steps.steps_2_value相同
  	/*
  	可添加多项自定义想要的数据
  	*/
  	item_3: [{ //item_3变量名需与下方steps.steps_3_item相同
  		name: "东湖", //name变量名需与下方steps.steps_3_value相同
  		/*
  		可添加多项自定义想要的数据
  		*/
  	}]
  }, {
  	value_2: "九江",
  	item_3: [{
  		"name": "德安"
  	}]
  }]
  }, {
  value_1: "山东",
  item_2: [{
  	value_2: "济南",
  	item_3: [{
  		name: "历下"
  	}],
  }, {
  	value_2: "青岛",
  	item_3: [{
  		name: "市南"
  	}]
  }]
  }],
  steps: {
  step_1_value: "value_1",
  step_2_value: "value_2",
  step_2_item: "item_2",
  step_3_value: "name",
  step_3_item: "item_3"
  },
  linkageNum: 3, //3 表示为3级联动
  linkage: true //true 表示开启联动
}
```

### 1.0.1.0.5 `custom2类型`

| 属性名| 是否必填| 值类型|  默认值| 说明|
| --------- | -------- | -----: | --: |
| itemArray| | Array| | 需循环展示的数据(无联动使用此属性) |
| itemObject| | Object| | 需循环展示的数据(联动使用此属性) |
| defaultValue| | Array| | 初始值 |
| linkage| | Boolean| `false`| 是否联动|
| linkageNum| | Number| | 联动级数|
| steps| | Object| | 自定义阶级变量名，详见下方示例与说明|

### 1.0.1.0.5.0.1 custom2的steps属性说明
| 属性名| 是否必填| 值类型| 默认值| 说明|
|------|----|----|----|-------|
| step_1_value| | String| | 一级显示属性名|
| step_2_value| |String| |二级显示属性名|
| step_3_value| | String| | 三级显示属性名|
注：详见下方示例

示例代码:

```javascript
{
  itemObject: {
  	step_1: [{
  		name: "江西"
  	}, {
  		name: "山东"
  	}],
  	step_2: [
  		["南昌", "九江"], //对应step_1的江西
  		["济南", "青岛"] //对应step_1的山东
  	],
  	step_3: [
  		[
  			[ //对应step_2的南昌
  				"东湖"
  			],
  			[ //对应step_2的九江
  				"德安"
  			]
  		],
  		[
  			[ //对应step_2的济南
  				"历下",
  			],
  			[ //对应step_2的青岛
  				"市南",
  			]
  		]
  	]
  },
  steps: {
  	step_1_value: "name", //第一级显示的属性名
  	step_2_value: "", //第二级显示的属性名
  	step_3_value: "" //第三级显示的属性名
  },
  defaultValue: [1, 0, 0], //初始数据
  linkageNum: 3, //3 表示为3级联动
  linkage: true //true 表示开启联动
}
```

## 1.0.2 buttonSet属性说明

| 值| 值类型| 默认值| 说明|
| --------- | -------- |
| cancelType| String| `default`| 取消按钮的类型 |
| confirmType| String| `primary`| 确定按钮的类型 |
| cancelStyle| cssStyle| | 取消按钮的样式, `只支持middle模式`|
| confirmStyle| cssStyle| | 确定按钮的样式, `只支持middle模式`|
| cancelName| String| `取消`| 取消按钮名称|
| confirmName| String| `确定`| 确定按钮名称|
|`v5.0更新`|  |   |   |
| cancleColor | Color| `#ADADAD`| 取消按钮的颜色，`不支持middle模式` |
| confirmColor| Color| `#3399FF`| 确定按钮的颜色，`不支持middle模式` |

## 1.0.3 mode属性说明

| 值| 说明|
| --------- | -------- |
| middel| 从中间渐出 |
| top| 从顶部弹出 |
| bottom| 从底部弹出(默认) |
