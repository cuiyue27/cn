
# 缓存
京东智联云安全加速SCDN支持缓存功能，该功能可以在距离访问者更近的地方提供资源，节省源站不必要的访问流量。

**缓存概述**

安全加速SCDN根据以下内容缓存静态内容：
- 域名访问者的来源
- 访问者可以到达哪个安全加速SCDN数据中心
- 访问者在特定数据中心请求资源频率

安全加速SCDN在以下情况下不缓存内容：

- DNS配置为（灰色）未代理状态


安全加速SCDN提供几种缓存自定义选项：

- 通过“缓存”页面调整缓存级别、TTL等
- 通过“页面规则”为各个URL指定缓存配置
- 通过“Workers”自定义缓存（Workers功能暂未上线 敬请期待）

针对不同套餐级别，缓存文件大小上限限制不同，具体可参考套餐规格。

**缓存文件类型**


安全加速SCDN通过文件扩展名缓存，SCDN将会自动缓存包含某些文件扩展名的文件，默认不缓存HTML。
如需缓存HTML内容，需要通过页面规则来缓存静态HTML内容。


bmp、ejs、jpeg、pdf、ps、ttf

class、eot、jpg、pict、svg、webp

css、eps、js、pls、svgz、woff

csv、gif、mid、png、swf、woff2

doc、ico、midi、ppt、tif、xls

docx、jar、otf、pptx、tiff、xlsx


**安全加速SCDN高速响应缓存**

Cache-Status标头输出显示资源是否缓存。
缺少标头的情况标明资源未缓存。

- HIT 在SCDN的缓存中找到资源
- MISS 未在SCDN缓存中找到资源，从源Web服务器获取
- EXPIRED 在SCDN缓存中找到资源但已过期，从源Web服务器获取
- STALE 资源通过缓存提供，但已经过期，SCDN无法获取源站检索更新后的资源
- BYPASS 源站通过设置为no-cache、private或max-age=0的Cache-Control标头指示源站绕过缓存。
- REWALIDATED 资源通过缓存提供，但已过时。已通过 If-Modified-Since 标头或 If-None-Match 标头重新验证资源。
- UPDATING 资源通过缓存提供，但已过期。资源目前正在由源Web服务器进行更新。

**缓存配置**
- 清除缓存

  清除缓存可能会暂时降低源站性能。安全加速SCDN支持全部缓存清除。
  也支持自定义清除。自定义清除支持以下几种方式：
  - URL，SCDN缓存中与URL完全匹配的任何资源都将从缓存中清除
  - 主机名，URL中其主机与提供值相匹配的任何资源都将从缓存中清除
  - 标记，由与提供值相匹配的Tag响应标头提供服务的任何资产都将从缓存中清除
  - 前缀，此目录中所有资源都将从缓存中清除



- 缓存级别
  通过缓存级别可以为静态内容设置缓存：
  - 标准，每次查询字符串更改时，都会提供不同资源

    如：example.com/pic.jpg?with=query
  - 基础，只有无查询字符串时，才从缓存中提供资源

    如：example.com/pic.jpg
  - 简单，即使是不同的查询字符串，依旧提供相同资源，即忽略

    如：example.com/pic.jpg?ignore=this-query-string


- 缓存TTL
    - 可修改缓存文件时长，如4小时、1小时、30分钟等