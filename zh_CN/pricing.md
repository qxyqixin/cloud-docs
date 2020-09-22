# 产品定价

EMQ X Cloud 按集群实例规格与消息传输网络流量收费，而非消息条数，不限 API 与规则引擎的使用，业务海量扩张的时候成本仍然清晰可控。



## 计费项目

EMQ X Cloud 按照部署规格（最大连接数、消息 TPS）对每个部署进行计费，不同规格有不同的小时单价。

创建部署前 EMQ X Cloud 会根据您的部署选用情况估算使用成本，具体价格可以前往[价格估算](https://cloud.emqx.io/cn/calculator)页面查看


具体计费项目见下表：

| 项目     | 描述                                                         |
| -------- | ------------------------------------------------------------ |
| <div style="width: 120px"></div>基础费用 | 根据部署规格（最大连接数、消息 TPS）确定，实际使用中该部分预估费用不会变动。 |
| 流量使用 | 基础费用已包含一定的流量，赠送流量当月有效，如有剩余月底自动清空；设备通信超出流量后超出部分将按照 1.5元/GB 收取。 |


{% hint style="danger" %}
注意: 由于实际使用情况不同，估计成本与实际成本之间可能存在差异。
{% endhint %}



### 计费周期

EMQ X Cloud **每小时**统计核算一次上小时内账户消费情况（小时账单）并从余额扣费，然后累加到当月消费（月账单），您可以前往[账单页面](<https://cloud.emqx.io/console/billing/overview>)查看详细扣费信息



### 欠费说明

余额不足时 EMQ X Cloud 将发送通知邮件到注册邮箱，期间提供一定数额透支额度，透支额度耗尽后将停止并删除您现有部署实例，造成的影响包括：

- 保留追回透支欠款的权利
- 清空部署运行数据，**丢失的数据无法恢复**。

{% hint style="danger" %}
注意: 透支额度默认为 10 元，您可以联系所属商务经理或者提交工单来提升额度
{% endhint %}

<!-- ### 计费示例一 TODO 等待添加 ### 计费示例二 -->