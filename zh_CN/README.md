# EMQ X Cloud 产品简介

EMQ X Cloud 作为全球首个全托管的 MQTT 5.0 公有云服务，提供了一站式运维代管、独有隔离环境的 EMQ X 接入平台服务。对于首次使用 EMQ X Cloud 的客户，我们为您准备了 **一次** 创建长达 **180** 天时长免费试用部署的机会。

EMQ X Cloud 为应用程序及物联网设备提供安全可靠的双向通信能力:

- 南向连接海量设备，支持设备数据上云、设备相互通信；
- 北向可以将设备事件与消息数据存储至各类数据库与流处理系统中，同时支持调用云端 API 将控制指令下发至设备。

借助云服务商提供的基础计算设施，EMQ X Cloud 面向全球数十个国家与地区提供服务，为 5G 与万物互联应用提供低成本、安全可靠的云服务。

![emqx_cloud](https://static.emqx.net/images/b7f3e53a4f6a789c698e5af8476d3e51.png)



### 产品能力

EMQ X Cloud 作为全托管的 EMQ X 接入平台服务，提供了设备接入、设备管理、消息存储等功能。

#### 设备接入

支持海量设备连接上云，提供设备与设备、设备与应用稳定可靠的双向通信能力。

- 支持标准的 MQTT 协议（包括 MQTT over WebSocket），使用标准 MQTT 客户端库即可连接上云
- 支持 CoAP、MQTT-SN、LwM2M 协议以及私有 TCP 协议接入，满足各类系统接入上云需求
- 提供不同网络设备、工业/边缘设备上云接入方案
- 开源多种语言/平台接入示例代码，提供跨平台移植指导
<!-- TODO: example 仓库 -->
- 完美契合 EMQ [边缘计算](https://www.emqx.io/cn/products/kuiper)、[边缘工业物联网](https://www.emqx.io/cn/products/neuron)产品生态，支持数十种工业协议接入上云

{% hint style="info" %}
多协议以及私有协议支持请[工单](./contact.md)联系进行开通。
{% endhint %}



#### 设备管理

为保证灵活性，EMQ X Cloud 不直接提供设备管理相关功能，而是通过 REST API 与规则引擎进行能力开放，用户可以选择需要的功能，与自己的设备管理系统、物联网平台集成。

![image (1)](https://static.emqx.net/images/64e6c6e9650c1f00b8376e7239343c4e.png)

- **设备认证信息管理：**平台通过 REST API 进行认证信息增、删、查、改

- **设备在线状态查看：**
  - 平台通过 REST API 获取在线设备列表，查询设备是否在线
  - 平台通过规则引擎在设备上线、下线时改写私有数据库中设备的状态或发送到自建服务（Web 服务）
- **设备离线告警：**设备离线时通知平台，判断是否需要告警
- **设备上下线历史记录：**
  - 平台通过规则引擎在设备上线、下线时将上下线信息写入私有数据库或发送到自建服务（Web 服务）
- **设备发布订阅 ACL 权限管理：**平台通过 REST API 对 ACL 权限进行增、删、查、改
- **在线设备踢下线：**平台将在线设备踢下线
- **代理订阅：**平台通过 REST API 为**在线设备**订阅或取消订阅主题
- **向设备发布消息：**平台通过 REST API 或 MQTT 接入向指定主题发布消息，支持批量操作
- **获取设备消息进行桥接/存储：**通过规则引擎，将设备事件（上下线、订阅/取消订阅、消息发布）以及消息数据存储至私有数据库（主流关系/非关系，各类时序数据库）、消息队列 Kafka 以及自建 Web 服务。
- **消息收发、连接数等业务统计：**通过 REST API 获取相关统计信息。



#### 消息存储（规则引擎）

EMQ X Cloud 支持使用规则引擎配置设备消息、事件的处理、响应规则。

规则引擎不仅提供了清晰、灵活的"配置式"的业务集成方案，简化了业务开发流程，提升用户易用性，降低业务系统与 EMQ X 的耦合度。

![](https://docs.emqx.net/broker/latest/cn/assets/image-20190506171815028.jpg)

- **发送到 HTTP 服务与其他 MQTT 服务**
  - 发送数据到 Web 服务
  - 桥接数据到 MQTT Broker

- **保存设备事件信息、消息数据到数据库，用设备事件驱动业务数据**
  - 保存数据到 MySQL
  - 保存数据到 PostgreSQL
  - 保存数据到 Cassandra
  - 保存数据到 MongoDB
  - 保存数据到 DynamoDB
  - 保存数据到 Redis
  - 保存数据到 ClickHouse
  - 保存数据到 TDengine
  - 保存数据到 OpenTSDB
  - 保存数据到 TimescaleDB
  - 保存数据到 InfluxDB

- **桥接数据到 Kafka、RabbitMQ 等消息与流处理平台**
  - 桥接数据到 Kafka
  - 桥接数据到 Pulsar
  - 桥接数据到 RocketMQ
  - 桥接数据到 RabbitMQ
  - 桥接数据到 RPC 服务

- **消费消息下发到设备，事务级的平台指令下发**
  - 从 Kafka 消费消息到 EMQ X
  - 从 Pulsar 消费消息到 EMQ X
  
  

### 使用限制

相比于 公有云 IoT Hub 平台，EMQ X Cloud 有更少的使用限制。下表中相关的限制取决于购买的连接数与硬件性能，对应的参数 EMQ 官方均进行过严密性能测试。

> 以下各表中 EMQ X 的“不限”指不做技术手段限制，相关项的性能取决于部署规格，具体数据以实际使用场景为准。

#### 连接通信

| **限制描述**         | **EMQ X**                                             | **公有云 IoT Hub**                     |
| -------------------- | ----------------------------------------------------- | -------------------------------------- |
| 最大同时在线长连接数 | 取决于规格，1000-1000W+ 可选，大于 20W 请工单联系申请 | 1W-50W                                 |
| 每秒建立连接次数     | 1W                                                    | 200-500                                |
| 单客户端订阅主题数   | 不限                                                  | 10-100                                 |
| 单客户端每秒订阅请求 | 不限                                                  | 10-1W                                  |
| 单客户端上行消息速度 | 不限                                                  | QoS0：30条/秒QoS1：10条/秒QoS2：不支持 |
| 单客户端消息下行     | 不限                                                  | 50-100条/s                             |
| 单客户端每秒吞吐带宽 | 不限                                                  | 512-1024KB                             |
| 单个消息长度         | 默认 1024KB 1-256MB 可申请调整                        | 256KB                                  |
| 离线消息最大存储时长 | 默认不限                                              | 1周                                    |

#### Topic 限制

| **限制描述**              | **EMQ X**          | **公有云 IoT Hub**                              |
| ------------------------- | ------------------ | ----------------------------------------------- |
| Topic 数量                | 不限               | 单产品50个                                      |
| 权限                      | 自定义任意主题权限 | 设备只能对自己的有限数量的Topic进行消息发布订阅 |
| 订阅/取消订阅操作响应时间 | 立即               | 5-10秒                                          |



### 产品优势

#### 协议支持完整

支持 MQTT v3.1，v3.1.1 与 v5.0 协议版本，是全球首个支持 MQTT 5.0 的公有云服务，支持 MQTT WebSocket 服务，完整支持 QoS0, QoS1 与 QoS2 级别 MQTT 消息。

#### 更少的使用限制

大部分公有云 IoT 平台有多方面的使用限制，包括 MQTT 主题数量、消息大小、消息速率以及接入/通信模式。EMQ X Cloud 拥有更少的使用限制，让您无阻碍地集成使用。

#### 显著的成本优势

按集群实例与消息流量收费，而非消息条数，不限 API 与规则引擎的使用，业务海量扩张的时候成本仍然清晰可控。


#### 完全托管的运维

数分钟内创建高可用 MQTT 集群立即开始设备接入，随后整个使用周期由我们的全球服务支持团队和 EMQ 专家提供 7*24 不间断的操作和运维服务，您可以随时通过工单，电子邮件，电话等快速获得响应。


#### 高可用性与数据安全

采用高冗余集群架构，以确保服务的高可用性；通过独有隔离环境保障您数据安全与业务稳定性，每个部署集群都有自己的公共 IP、专用 VPC 网络、独立 EMQ X 服务器与数据库服务器，这更安全，更可靠。


#### 多种协议接入，私有化定制功能扩展

支持包含 MQTT、MQTT-SN、CoAP、LwM2M、私有 TCP 协议在内的多种通信协议接入，覆盖各类行业应用；可根据您的特殊使用场景定制私有化功能，充分契合业务需求。


#### 容量预估与伸缩

通过连接数与消息吞吐量自动预估容量，通过紧密的监控来制定伸缩计划，集群大小可随业务规模平滑调整。


#### 灵活的数据流转方案

支持实时预处理设备事件与消息数据，并存储到云上 MySQL、Kafka、InfluxDB 等十余种数据库与消息系统中。
