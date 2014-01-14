---
layout: docs
title: 图片主色调（imageAve）
order: 173
---

<a id="imageAve"></a>
# 图片主色调（imageAve）

<a id="imageAve-description"></a>
## 描述

图片主色调为一幅图片的平均色调。  
在图片下载URL后附加`imageAve`指示符（区分大小写），即可获取JSON格式的图片主色调。  

---

<a id="imageAve-request"></a>
## 请求

<a id="imageAve-request-syntax"></a>
### 请求报文格式

```
GET <imageDownloadUri>?imageAve HTTP/1.1
Host: <imageDownloadHost>
```

<a id="imageAve-request-header"></a>
### 请求头部

头部名称       | 必填 | 说明
:------------- | :--- | :------------------------------------------
Host           | 是   | 下载服务器域名，可为七牛三级域名或自定义二级域名，参考[域名绑定][cnameBindingHref]

---

<a id="imageAve-response"></a>
## 响应

<a id="imageAve-response-syntax"></a>
### 响应报文格式

```
HTTP/1.1 200 OK
Content-Type: application/json
Cache-Control: no-store

{
    "RGB":       "<RGB hex string>",
}
```

<a id="imageAve-response-header"></a>
### 响应头部

头部名称       | 必填 | 说明
:------------- | :--- | :------------------------------------------
Content-Type   | 是   | MIME类型，固定为application/json
Cache-Control  | 是   | 缓存控制，固定为no-store，不缓存

<a id="imageAve-response-content"></a>
### 响应内容

■ 如果请求成功，返回包含如下内容的JSON字符串（已格式化，便于阅读）：  

```
{
    "RGB":       "<RGB hex string>",
}
```

字段名称       | 必填   | 说明
:------------- | :----- | :------------------------------
RGB         | 是     | RGB值，hex字符串格式

■ 如果请求失败，返回包含如下内容的JSON字符串（已格式化，便于阅读）：  

```
{
	"code":     <httpCode  int>, 
    "error":   "<errMsg    string>",
}
```

字段名称     | 必填 | 说明                              
:----------- | :--- | :--------------------------------------------------------------------
`code`       | 是   | HTTP状态码，请参考[响应状态](#imageAve-response-status)
`error`      | 是   | 与HTTP状态码对应的消息文本


<a id="imageAve-samples"></a>
## 示例

1. 获取图片主色调：  

	在Web浏览器中输入以下图片地址  

	```
    http://qiniuphotos.qiniudn.com/gogopher.jpg?imageAve
	```

	返回结果（内容经过格式化以便阅读）  

	```
    {
        "RGB":   "0xc79d73"
    }
	```

<a id="imageAve-internal-resources"></a>
## 内部参考资源

- [域名绑定][cnameBindingHref]

[sendBugReportHref]:            mailto:support@qiniu.com?subject=599错误日志     "发送错误报告"
[cnameBindingHref]:             http://kb.qiniu.com/53a48154                     "域名绑定"
