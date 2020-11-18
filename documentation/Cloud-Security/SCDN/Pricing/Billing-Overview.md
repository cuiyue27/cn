# 计费概述
京东智联云SCDN采用混合计费方式，具体如下：

 **计费组成**

京东智联云SCDN产品计费项由以下几部分组成。

| 计费项目 | 是否必选 | 付费方式 | 规则         | 说明                                                                     |
| ---------- | -------- | -------- | -------------- | -------------------------------------------------------------------------- |
| SCDN套餐 | 是      | 预付费 | 按月/包年购买 | 基础产品套餐费用，通常由加速带宽、防护带宽、域名数量、CC防御数量等费用构成 |
| CDN服务  | 是      | 后付费 | 流量计费      | 超出套餐外的实际SCDN流量进行计费 |
| 弹性防护 | 是      | 后付费 | 阶梯计费   | 按照实际DDoS/CC弹性防护峰值，对应阶梯计费价格           |
| 域名扩展包 | 否      | 预付费 | 预付费包年包月 | 按业务情况选购，到期时间与安全加速到期时间一致，支持自动续订 |


说明：


支持流量计费和带宽峰值流量计费两种模式，默认采用流量计费。

按天计费，计费周期为每天0时-24时，每天6时，进行前一天的账单结算。

+ 流量计费：按实际使用的流量计费，单位为GB，每日扣费、按月阶梯，每次计费时，对用户在本次计费周期中产生的流量进行自然月阶梯计费。
+ 带宽峰值计费：按使用的带宽峰值计费，每5分钟统计一个带宽，每天共统计288个点，每次计费时，对用户在本次计费周期中的带宽最大值(带宽峰值)进行日阶梯计费。